---
title: var, let, const
---

```javascript
a = 1
var a = 1
let a = 1
const a = 1
```

## a=1 声明了一个全局变量是错的

```javascript
a = 1
console.log(window.a)
// 声明了一个全局变量
```

```javascript
var a
function f1(){
    var a
    functon f2(){
        a = 1 // 如果函数外有声明过 a 的话该表达式不会声明一个全局变量
    }
}

f1()
```

`a = 1` 含义不明，不建议用。

## var a = 1

var 会变量提升

```javascript
function fn(){
    if(true){
        console.log(a) // undefined 不会报错
    }else{
        var a
        console.log(2)
    }
}
fn()
```

```javascript
function x(){
    var a = 1
    window.frank = function(){
        console.log(a)
    }
}
// 目的：只暴露 frank 一个全局变量
// 但函数名 x 也是一个全局变量
// 隐藏了 a 变量
```

## 立即执行函数（IIFE）


```javascript
(function(){
    var a = 1
    window.frank = function(){
        console.log(a)
    }
}())
// 目的：只暴露 frank 一个全局变量
// 隐藏了 a 变量
```

## let

方便地使用局部变量而且不需要引入一个函数。

```javascript
{
    let a = 1
    window.frank = function(){
        console.log(a)
    }
}
console.log(a) // 报错
```

## 块级作用域

```javascript
{
    let a = 1
}
console.log(a) // 报错
```

```javascript
{
    var a = 1
}
console.log(a) // 1
```

```javascript
{
    let a = 1
    {
        let a = 2
        {
            let a = 3
            console.log(a) // 3
        }
    }
}
```

```javascript
{
    let a = 1
    {
        let a = 2
        {
            console.log(a) // 报错
            let a = 3
        }
    }
}
```

1. let 的作用域在两个花括号{}之间

2. 在 let a 之前使用a ，报错

3. 如果重复 let a ，报错

## const

```javascript
const a = 2
a = 3 // 报错
```

1. const 的作用域在两个花括号{}之间

2. 在 const a 之前使用a ，报错

3. 如果重复 const a ，报错

4. 只有一次赋值机会，而且必须在声明时赋值

## 小题

```javascript
var a = 1
function fn(){
    console.log(a)
}
a = 2
fn() // 2
```

```javascript
for(var i = 0; i < 6; i++){

}
console.log(i) // 6
```

```javascript
var i
for(i=0;i<6;i++){
    function fn(){
        console.log(i)
    }
    fn() // 1,2,3,4,5 
}
console.log(i) // 6
```

```javascript
var i
for(i=0;i<6;i++){
    function fn(){
        console.log(i)
    }
    button.onclick = fn // 6 
}
console.log(i) // 6
```

## 面试题

```html
<ul>
    <li>1</li>
    <li>2</li>
    <li>3</li>
    <li>4</li>
    <li>5</li>
    <li>6</li>
</ul>
```

```javascript
var liTags = document.querySelectorAll('li')
for(var i = 0;i <liTags.length;i++){
    liTags[i].onclick = function(){
        console.log(i) // 点击任何一个 li 都返回最后一个 i+1，即 liTags.length
    }
}
```

解决方法一：

```javascript
var liTags = document.querySelectorAll('li')
for(var i = 0;i <liTags.length;i++){
    let j = i
    liTags[j].onclick = function(){
        console.log(j)
    }
}
```


解决方法二：

```javascript
var liTags = document.querySelectorAll('li')
for(var i = 0;i <liTags.length;i++){
    (function(){
        var j = arguments[0]
        liTags[j].onclick = function(){
            console.log(j)
        }
    })(i)
}
```

```javascript
var liTags = document.querySelectorAll('li')
for(var i = 0;i <liTags.length;i++){
    (function(j){
        liTags[j].onclick = function(){
            console.log(j)
        }
    })(i)
}
```

解决方法三：

let 的魔法

```javascript
var liTags = document.querySelectorAll('li')
for(let i = 0;i <liTags.length;i++){
    liTags[i].onclick = function(){
        console.log(i)
    }
}
```