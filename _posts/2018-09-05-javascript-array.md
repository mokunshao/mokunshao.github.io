---
title: JavaScript Array 学习笔记
---

加不加 `new` 对 `Array` 都一样

```javascript
// 以下两者的效果是一样的
var a = Array(3)
var a = new Array(3)    
```

情况一：

```javascript
var a = Array(3)
// 生成一个对象，length属性为3
a.length
// 3
a
// (3) [empty × 3]
a.push 
// f push() {[native code]}
"0" in a
// false
a.__proto__===Array.prototype
//true
```

情况二：

```javascript
var b = Array(3,3)
// 生成一个对象，此时的情况和第一种不同，length属性为2
b.length
// 2
a
// (2)[3,3]
```

1. 基本数据类型对应的构造函数（例如 `number`、`string`、`Boolean`）

不加 `new` 返回基本数据类型

加 `new` 返回对象

2. 复杂数据类型（例如 `object`、`array`、`function`）

加 `new` 和不加 `new` 都一样

```javascript
var f = function(a,b){
    return a+b
}
// 等价于
var f = new function('a','b','return a+b')
```

`function` 是关键字

`Function` 是全局对象

函数声明方法有：具名函数、匿名函数、构造函数。

伪数组是指原型链中没有 `Array.Prototype` 的对象。

## Array 对象内置方法

- forEach

无返回值

- sort

改变自身的值

- join

- concat

- map

映射

和forEach几乎一样

相比forEach有返回值，返回一个新数组

- filter

过滤

跟map很像

- reduce

## map 可以用 reduce 表示

```javascript
a=[1,2,3]
a.reduce(function(arr,n){
    arr.push(n*2)
    return arr
},[])

// 返回 [2,4,6]
```

## filter 可以用 reduce 表示

```javascript
a=[1,2,3,4,5,6,7,8,9,10]
a.reduce(function(arr,n){
    if(n%2===0){
        arr.push(n)
    }return arr
    },[])
// 返回 [2, 4, 6, 8, 10]    
```

## 题目

1. 第一题
```
var students = ['小明','小红','小花'] 
var scores = { 小明: 59, 小红: 99, 小花: 80 } 
students.sort(???)
请填写 ??? 使得 students 按分数的高低从大到小排列
```
```javascript
// 答案一：
function(x,y){return scores[y]-scores[x]}
// 答案二：
function(a,b){
    return scores[b] - scores[a]
}
```
2. 第二题

```
var a = [1,2,3,4,5,6,7,8,9]
a.filter(???).map(???) // [4,16,36,64]
1. 获取所有偶数
2. 得到所有偶数的平方
```

```javascript
// 答案一：
var a = [1,2,3,4,5,6,7,8,9]
a.filter(function(n){if(n%2===0);return n}).map(function(x){return x*x}) // [4,16,36,64]

// 答案二：
var a = [1,2,3,4,5,6,7,8,9]
a.filter( (n)=>n%2===0 ).map(  (n)=> n*n  ) // [4,16,36,64]
```

3. 第三题

```javascript
var a = [1,2,3,4,5,6,7,8,9]
a.reduce(???,???)
计算所有奇数的和
```
```javascript
// 答案一：
var a = [1,2,3,4,5,6,7,8,9]
a.reduce(function(arr,n){
    if(n%2===1){
        return arr+n
    }else{
    return arr
    }}, 0)

// 答案二：
var a = [1,2,3,4,5,6,7,8,9]
a.reduce(  (sum,n)=> {
    return n%2===1 ? sum + n : sum
}  ,0)
```