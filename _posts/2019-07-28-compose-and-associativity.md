---
title: 函数组合和结合律
---

## 函数组合 Compose

函数组合又称为饲养函数，是若干个纯函数、偏函数、柯里化函数组合成一个新的函数，形成数据传递，并实现一种有序执行的效果。

```javascript
function toUpperCase(str) {
  return str.toUpperCase()
}
function exclaim(str) {
  return str+'!'
}
function compose(fn1,fn2) {
  return function (x) {
    return fn1(fn2(x)) // 左倾
  }
}
var fn3 = compose(prefix,exclaim)

console.log(fn3('hello'))
// HELLO!
```

优化版本，可接受无限个参数：

```javascript
function toUpperCase(str) {
  return str.toUpperCase()
}
function exclaim(str) {
  return str+'!'
}
function prefix(str) {
  return "I said " + str;
}
function compose() {
  var args = Array.prototype.slice.call(arguments);
  var index = args.length - 1;
  return function(x) {
    var res = args[index](x);
    while (index--) {
      res = args[index](res);
    }
    return res;
  };
}
var fn3 = compose(prefix,exclaim,toUpperCase)

console.log(fn3('hello'))
// I said HELLO!
```

进一步优化的版本：

```javascript
function toUpperCase(str) {
  return str.toUpperCase()
}
function exclaim(str) {
  return str+'!'
}
function prefix(str) {
  return "I said " + str;
}
function compose() {
  var args = Array.prototype.slice.call(arguments);
  return function(x) {
    return args.reduceRight(function(res, cb) {
      return cb(res);
    }, x);
  };
}
var fn3 = compose(prefix,exclaim,toUpperCase)

console.log(fn3('hello'))
// I said HELLO!
```

## 结合律 Associativity

结合律就是在组合函数的参数中对参数进行函数组合。

以下三个的执行结果完全一样。

```javascript
var fn1 = compose(prefix,exclaim,toUpperCase)
var fn2 = compose(compose(prefix,exclaim),toUpperCase)
var fn3 = compose(prefix,compose(exclaim,toUpperCase))
fn1('hello') === fn2('hello'); // true
fn1('hello') === fn3('hello'); // true
fn3('hello') === fn2('hello'); // true
```