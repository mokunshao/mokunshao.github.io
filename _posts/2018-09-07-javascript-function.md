---
title: JavaScript Function 学习笔记
---

JavaScript 具有不一致性

```javascript
function y(){}
console.log(y)
// y(){}

var x = function y(){}
console.log(y)
// 报错
```

## 五种函数声明

```javascript
function x(){}
var a = function(){}
var a = functionx(){}
var a = new Function()
var a = (x,y)=>{}
```

## name 属性

```javascript
function f(){}
f.name
// "f"

var  f2 = function(){}
f2.name
// "f2"

var  f3 = function f4(){}
f3.name
// "f4"

var f5 = new Function()
f5.name
// "anonymous"
```

## 用 Object 实现一个 Function

```javascript
var f = {}
f.params = ['x','y']
f.functionBody='console.log('fff')'
f.call=function(){
    return window.eval(f.functionBody)
}

f(1,2)===f.call(undefind,1,2)
```

## this 和 arguments

在严格模式下

在 `a.call(undefind,1,2)` 中

this 为第一个参数

arguments 为其余参数

而在非严格模式下 this 为 window 对象

```javascript
function f(){
    'use strict'
    console.log(this)
    console.log(arguments)
    return undefined
}
f.call(1,2,3) // this 为 1，arguments 为 [2,3]
```

## 作用域

JavaScript 拥有链式作用域机制（父作用域是可以被其子作用域访问的，而子作用域却不能被父作用域访问）。

做题前请先提升声明。

```javascript
var a = 1
function f1(){
    alert(a) // 是多少
    var a = 2
}
f1.call()
// undefined
```

```javascript
var a = 1
function f1(){
    var a = 2
    f2.call()
}
function f2(){
    console.log(a) // 是多少
}
f1.call()
// 1
```

```javascript
var liTags = document.querySelectorAll('li')
for(var i = 0; i<liTags.length; i++){
    liTags[i].onclick = function(){
        console.log(i) // 点击第3个 li 时，打印 2 还是打印 6？
    }
}
// 6
```
## 闭包

如果一个函数，使用了它范围外的变量，那么（这个函数+这个变量）就叫做闭包。

闭包会让他所在作用域中的变量始终保存在内存中，而不会被垃圾回收机制回收。

## 题目

```javascript
var f1 = function f2(){}
f1.name // 是多少？
// 'f2'
```

```javascript
var f1 = function f2(){}
f2.name // 是多少
// f2 is not defined
```

```javascript
var f1 = function f2(){}
console.log(f2)
// 打印出多少
 // f2 is not defined（f2 不存在，而且 f2 不是 undefined）
```

```javascript
function f(){
console.log(this)
}
f.call(1)
// 打印出多少？
// Number 对象 1
```

```javascript
function f(){
'use strict'
console.log(this)
}
f.call(1)
// 打印出多少？
// 1
```

```javascript
function f(){
console.log(this)
}
f.call()
// 打印出什么
// window
```

```javascript
function f(){
'use strict'
console.log(this)
}
f.call()
// 打印出什么
// undefined
```

```javascript
var a = console.log(1)
a // a 的值是什么？
// undefined
```

```javascript
function f(){
return 1
}
a = f
a // a 的值是什么
// 函数 f
```

```javascript
function f(){
return 1
}
var a = f.call()
a // a 的值是什么？
// 1
```

```javascript
var a = 1,2
a //a 的值是什么
// 报错
```

```javascript
var a = (1,2)
a //a 的值是什么
// 2
```

```javascript
var a = (1, console.log(2))
a // a 的值是什么
//undefined
```

```javascript
function f(){
return function f2(){}
}
var a = f.call()
a // a 的值是什么？
// 函数f2
```

```javascript
function f(){
return function f2(){}
}
var a = f.call()
var b = a.call()
b //b 的值是什么？
// undefined
```

```javascript
function f(){
return function f2(){}
}
var a = f.call().call()
a // a 的值是什么？
// undefined
```

```javascript
function f1(){
    console.log(this)
    function f2(){

    }
}
var obj = {name: 'obj'}
f1.call( obj )
// 打印出什么
// obj对象
```

```javascript
function f1(){

    function f2(){
        console.log(this)
    }
    f2.call()
}
var obj = {name: 'obj'}
f1.call( obj )
// 打印出什么
// window 对象
```

```javascript
function f1(){
    console.log(this) // 第一个 this
    function f2(){
        console.log(this) // 第二个 this
    }
    f2.call()
}
var obj = {name: 'obj'}
f1.call( obj )
// 为什么两个 this 值不一样？
// 每个函数都有自己的 this，为什么会一样？
// this 就是 call 的第一个参数，第一个 this 对应的 call 是 f1.call(obj)，第二个 this 对应的 call 是 f2.call()
// this 和 arguments 都是参数，参数都要在函数执行（call）的时候才能确定
 ```