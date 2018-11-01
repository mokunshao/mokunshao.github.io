---
title: JavaScript 基础知识考试
---

第一题：

填空题

```javascript
var object = {}
object.__proto__ ===  ????填空1????  // 为 true

var fn = function(){}
fn.__proto__ === ????填空2????  // 为 true
fn.__proto__.__proto__ === ????填空3???? // 为 true

var array = []
array.__proto__ === ????填空4???? // 为 true
array.__proto__.__proto__ === ????填空5???? // 为 true

Function.__proto__ === ????填空6???? // 为 true
Array.__proto__ === ????填空7???? // 为 true
Object.__proto__ === ????填空8???? // 为 true

true.__proto__ === ????填空9???? // 为 true

Function.prototype.__proto__ === ????填空10???? // 为 true
```

```javascript
var object = {}
object.__proto__ ===  Object.prototype  // 为 true

var fn = function(){}
fn.__proto__ === Function.prototype  // 为 true
fn.__proto__.__proto__ === Object.prototype // 为 true

var array = []
array.__proto__ === Array.prototype // 为 true
array.__proto__.__proto__ === Object.prototype // 为 true

Function.__proto__ === Function.prototype // 为 true
Array.__proto__ === Function.prototype // 为 true
Object.__proto__ === Function.prototype // 为 true

true.__proto__ === Boolean.prototype// 为 true

Function.prototype.__proto__ === Object.prototype // 为 true
```

第二题：

```javascript
function fn(){
    console.log(this)
}
new fn()
```

new fn() 会执行 fn，并打印出 this，请问这个 this 有哪些属性？这个 this 的原型有哪些属性？

this 的属性只有 `__proto__`。 

```javascript
fn.__proto__ === Function.prototype
```

this 的原型的属性有 `constructor` 和 `__proto__`。 

```javascript
Function.prototype.__proto__ === Object.prototype
```

第三题：

```
JSON 和 JavaScript 是什么关系？
JSON 和 JavaScript 的区别有哪些？
```

### 关系：

JavaScript 是一种流行的脚本语言。

JSON 是一种数据交换格式，是 JavaScript 的一个子集，采用完全独立于语言的文本格式。

JSON 和 JavaScript 对象的字面量写法相似。

### 区别：

JSON 的数据类型有 object，array，string，number，boolean，null。

Javascript 的数据类型除了 JSON 所拥有的以外还有 undefined，function 和 symbol。

JSON 中的字符串必须用双引号括起，JavaScript 中字符串单双引号都可以。

JSON 中没有变量，所以不能引用，JavaScript中有变量，可以引用。

JSON 中没有原型链，JavaScript有原型链。

第四题：

```
前端 MVC 是什么？（10分）
请用代码大概说明 MVC 三个对象分别有哪些重要属性和方法。（10分）
```

### MVC 是什么？

MVC（Model-View-Controller）是一种架构模式。它根据代码的分工进行分类。

View 负责视图。

Model 负责数据。

Controller 负责处理事件和业务逻辑。

Controller 监听 View，用户对 View 做出了操作后，Controller 会去调用 Model，Model 与服务器交互，得到数据后返回数据给 Controller，Controller 根据接收到的数据更新 View 视图。

### 代码示例

View 主要接受一个选择器，获取需要监听的区域，然后返回一个对象给 Controller 操作、更新。

```javascript
window.View = function(selector){
    return this.document.querySelector(selector)
}
```

Model 主要负责数据库的初始化、数据的存储和获取，它的方法应该要有 init 、fetch 、save。

```javascript
window.Model = function(options){
    //通过传入参数获取需要操作数据库
    var resourceName = options.resourceName
    return {
        //初始化数据库
        init:function(){},

        //获取数据：
        fetch:function(){},

        //保存数据
        save:function(){}
        }
}
```

Controller 负责监听和更新 View，调用 Model 和接受 Model 返回的数据，它应该要有一个 init 方法接收传入的 View 和 Model，并进行初始化和绑定事件操作。

```javascript
window.Controller = function(options){

    var init = options.init

    var object = {
        view:null,
        model:null,
        init:function(view,model){
            this.view = view
            this.model = model
            this.model.init()
            init.call(this,view,model)
            this.bindEvents.call(this)
        },
    }

    //通过遍历传入的参数，将其添加到 object 对象中
    for(let key in options){
        if(key !== "init"){
            object[key]=options[key]
        }
    }
    
    return object
}
```

第五题：

```
在 ES5 中如何用函数模拟一个类？（10分）
```

```javascript
function Human(name,city){
    this.name = name
    this.city = city
}
Human.prototype = {
    constructor: Human,
    walk: function(){} ,
    species: function(){} ,
    useTools: function(){} ,
}
```

## 构造函数法

```javascript
function People(name) {
    this.name = name;
}

People.prototype.alive = true;

var xiaoming = new People('小明');
```

## `Object.create()`法

```javascript
var Chinese = {
    nation: "China",
    alive: true
};

var xiaoming = Object.create(Chinese);
```

## 极简方法

```javascript
var Chinese = {
    createNew: function(){
        var chinese = {};
        chinese.nation = "China";
        chinese.alive = true;
        return chinese;
    }
};

var xiaoming = Chinese.createNew();
```

第六题：

```
用过 Promise 吗？举例说明。
如果要你创建一个返回 Promise 对象的函数，你会怎么写？举例说明。
```

使用过，之前自制 jQuery.ajax 的时候,使用 promise 代替直接传入回调函数。使用 LeanCloud 的时候，从数据库获取和保存数据的时候也使用过。

```javascript
let test = function(){
    return new Promise(function(resolve, reject){
        if(Math.random() < 0.5){
            resolve('success')
        }else{
            reject('fail')
        }
    })
}
```