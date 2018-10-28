---
title: call、apply、bind 的用法分别是什么？
---

apply 、 call 、bind 的第一个参数都是 this，都可以改变 this 对象的指向。

```javascript
function f1(){
    console.log(this);
}

function f2(){}

f1.call(f2);  // function f2(){}
f1.apply(f2);  // function f2(){}
f1.bind(f2)();  // function f2(){}
```

```javascript
var ken = { 
    name: 'ken', 
    age: 20, 
    getName: function() {
        console.log(this.name);
    }
}

var tom = { name: 'tom', age: 20 }

ken.getName(); // ken

// tom 对象没有 getName 方法，但是可以通过 call/apply/bind 去使用 ken 对象的 getName 方法

ken.getName.call(tom);  // tom 
ken.getName.apply(tom); // tom
ken.getName.bind(tom)(); // tom
```

## call

除了 this，call 可以接受多个参数。

语法：

```javascript
fun.call(thisArg[, arg1[, arg2[, ...]]])
```

例子：

```javascript
function add(a,b){
    return a+b;
}
add.call(add, 5, 3); //8
```

## apply

除了 this，apply 接受一个数组作为参数。

语法：

```javascript
fun.apply(thisArg[, argsArray])
```

例子：

```javascript
function add(a,b){
    return a+b;
}
add.apply(add, [5, 3]); //8
```

## bind

bind()方法会创建一个新函数，称为绑定函数。

这个函数可以有预设的参数，也可以不预设参数，等调用的时候再传参。

bind 是返回对应函数，便于稍后调用，而apply 、call 则是立即调用 。

语法：
```javascript
fun.bind(thisArg[, arg1[, arg2[, ...]]]);
```

例子：

```javascript
function add(a, b){
    return a+b;
}

add.bind(add, 5,3)(); // 8
add.bind(add)(5,3); // 8
```

## 区别

相同之处：

1. 都是用来改变函数的 this 对象的指向的。

2. 第一个参数都是this要指向的对象。

3. 都可以利用后续参数传参。

不同之处：

1. call 和 apply接受参数的方式不一样，call 可以接受多个参数，apply 接受一个数组作为参数。

2. bind 是返回对应函数，便于稍后调用，而 apply 、call 则是立即调用 。

## 解决一个 Bug

```javascript
bindEvents: function () {
    function () {
        this.form.addEventListener('submit',  function(e) {
            e.preventDefault();
            this.saveMessage();
        })
    }
},
```

this.saveMessage 中的 this 是表单元素，不符合我们的预期。

解决方法一：

```javascript
bindEvents: function () {
    function () {
        this.form.addEventListener('submit',  (e) => { // 箭头函数不会改你的this
            e.preventDefault();
            this.saveMessage();
        })
    }
},
```

解决方法二：

```javascript
bindEvents: function () {
    function () {
        this.form.addEventListener('submit',  function(e) {
        e.preventDefault();
        this.saveMessage();
        }.bind(this))
    }
},
```