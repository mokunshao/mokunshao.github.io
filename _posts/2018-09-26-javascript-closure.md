---
title: JavaScript 的闭包
---

## 什么是闭包

1. 函数连同它作用域链上的要找的变量，共同构成闭包。

2. 闭包就是能够读取其他函数内部变量的函数。

3. 「函数」和「函数内部能访问到的变量」（也叫环境）的总和，就是一个闭包。

由于在Javascript语言中，只有函数内部的子函数才能读取其局部变量，因此可以把闭包简单理解成“定义在一个函数内部的函数”。

在本质上，闭包就是将函数内部和函数外部连接起来的一座桥梁。

不必要的闭包只会徒增内存消耗，因此不能滥用闭包，否则会造成网页的性能问题。

## 闭包的用途

### 1. 可以在函数外部读取函数内部声明的变量

```javascript
function f1() {
    var n = 999;
    function f2() {
        console.log(n);
    }
    return f2;
}

var result = f1();
result(); // 999
```

### 2. 让变量始终保持在内存中

让变量始终保持在内存中，即闭包可以使得它诞生环境一直存在，防止被垃圾回收。闭包使得内部变量记住上一次调用时的运算结果。

```javascript
function a(n) {
    return function () {
        return n++;
    };
}

let b = a(5);

b() // 5
b() // 6
b() // 7
```

```javascript
function add(){
    let a =0;
    function b(){
        a++;
        console.log(a);
    }
    return b;
}

let ab = add();

ab(); //1
ab(); //2
```

```javascript
let ab = (function add(){
    let a = 0;
    function b(){
        a++;
        console.log(a);
    }
    return b;
})()

ab(); //1
ab(); //2
```
### 3. 利用闭包实现 onclick 事件传递参数。

以下代码会使得点击不同的 li 都返回同一个值，这不是我们想要的结果。

```javascript
var lis = document.getElementsByTagName('li')
for(var i=0; i<lis.length; i++){
    lis[i].onclick=function(){
        alert(i)
    }
}
```

以上问题借助闭包可破。

```javascript
var lis = document.getElementsByTagName('li')
for(var i=0; i<lis.length; i++){
    lis[i].onclick=(function(i){
        return function(){
            alert(i)
        }
    })(i)
}
```

或者只是简单地把 var 改为 let，也可以解决问题，虽然不涉及闭包。

```javascript
let lis = document.getElementsByTagName('li')
for(let i=0; i<lis.length; i++){
  lis[i].onclick=function(){
        alert(i)
    }
}
```

### 4. 封装对象的私有属性和私有方法

```javascript
var Car = (function(){
    var speed = 0;
    function set(s){
        speed = s
    }
    function get(){
        return speed
    }
    function speedUp(){
        speed++
    }
    function speedDown(){
        speed--
    }
    return {
        setSpeed: setSpeed,
        get: get,
        speedUp: speedUp,
        speedDown: speedDown
    }
})()

Car.set(30)
Car.get() //30
Car.speedUp()
Car.get() //31
Car.speedDown()
Car.get()  //30
```

```javascript
function Person(name) {
    var age;
    function setAge(n) {
        age = n;
    }

    function getAge() {
        return age;
    }

    return {
        name: name,
        getAge: getAge,
        setAge: setAge
    };
}

var p1 = Person('张三');
p1.setAge(25);
p1.getAge() // 25
```

```javascript
function user(name){
    var age, sex;
    return{
        getName: function(){
            return name;
        },
        setName: function(newName){
            name = newName;    
        },    
        getAge: function(){
            return age;
        },
        setAge: function(newAge){
            age = newAge;
        },
        getSex: function(){
            return sex;
        },
        setSex: function(newSex){
            sex = newSex;
        }
    }
}

var xm = user('小明')
xm.setSex('男')
xm.setAge(22)
var name = xm.getName()
var sex = xm.getSex()
var age =xm.getAge()
console.log(name, sex, age) //小明 男 22
```