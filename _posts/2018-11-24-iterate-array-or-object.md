---
title: 遍历数组或对象
---

数组和对象都能用：

## for 循环

（不会忽略 undefined）

```javascript
for (var i = 0; i < arr.length; i++) {
    console.log(arr[i])
}
```

## for in 循环

```javascript
for (var key in arr) {
    console.log(arr[key])
}
```

## for of 循环

（不会忽略 undefined）

```javascript
for (var value of arr) {
    console.log(value)
}
```

## forEach 循环

这是数组的方法。

```javascript
arr.forEach(function (value) {
    console.log(value)
})
```

## arguments

```javascript
function print() {
    console.log(arguments)
}
```

## 伪数组（类数组对象）使用数组的方法来遍历

所谓伪数组只是看起来像数组，key 为从 0 开始的数字，也有 length 属性，实际上为对象。

方法一：

展开语法可以把伪数组（或者说“类数组对象”）转变为数组。

```javascript
[...arguments]
```

```javascript
function print() {
    [...arguments].forEach((value) => {
        console.log(value)
    })
}

print(1, 23)
```

方法二：

```javascript
function print1() {
    Array.from(arguments).forEach((value) => {
        console.log(value)
    })
}

print1(12, 6)
```

方法三：

```javascript
function print2() {
    Array.prototype.forEach.call(arguments, function (value) {
        console.log(value)
    })
}

print2(88, 77)
```