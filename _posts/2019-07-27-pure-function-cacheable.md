---
title: 纯函数的可缓存性
---

例子一：

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

优化后的例子一：

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

例子二：

```javascript
function memorize(fn) {
  var cache = {};
  return function() {
    var key = JSON.stringify(Array.prototype.slice.call(arguments));
    console.log(key)
    if (key in cache) {
      console.log("缓存了");
      return cache[key];
    } else {
      console.log("没缓存");
      return (cache[key] = fn.apply(this, arguments));
    }
  };
}

function add(a, b) {
  return a + b;
}

var memorizeAdd = memorize(add);

console.log(memorizeAdd(1, 2));
console.log(memorizeAdd(1, 2));

function propValue(obj) {
  return obj.value;
}

var memorizePropValue = memorize(propValue);

console.log(memorizePropValue({ value: 1 }));
console.log(memorizePropValue({ value: 1 }));

function fibonacci(n) {
  return n < 2 ? n : fibonacci(n - 1) + fibonacci(n - 2);
}

fibonacci = memorize(fibonacci);

console.log(fibonacci(100));

```