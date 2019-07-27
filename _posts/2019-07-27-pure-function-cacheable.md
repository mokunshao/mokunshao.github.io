---
title: 纯函数的可缓存性
---

例子：

```javascript
function test(fn) {
  var cache = {};
  return function() {
    var args = JSON.stringify(arguments);
    cache[args] = cache[args] ? cache[args] + "来自缓存池" : fn(arguments);
    return cache[args];
  };
}

var add = test(function(arguments) {
  var argLen = arguments.length;
  var item;
  var res = 0;
  for (var i = 0; i < argLen; i++) {
    item = arguments[i];
    res += item;
  }
  return res;
});

console.log(add(1, 2));
console.log(add(1, 2));
console.log(add(1, 3));
console.log(add(1, 3));
// 3
// 3来自缓存池
// 4
// 4来自缓存池
```

优化后的例子：

```javascript
function test(fn) {
  var cache = {};
  return function() {
    var args = JSON.stringify(arguments);
    cache[args] = cache[args] ? cache[args] + "来自缓存池" : fn.apply(fn,arguments);
    return cache[args];
  };
}

var add = test(function() {
  var argLen = arguments.length;
  var item;
  var res = 0;
  for (var i = 0; i < argLen; i++) {
    item = arguments[i];
    res += item;
  }
  return res;
});

console.log(add(1, 2));
console.log(add(1, 2));
console.log(add(1, 3));
console.log(add(1, 3));
// 3
// 3来自缓存池
// 4
// 4来自缓存池
```