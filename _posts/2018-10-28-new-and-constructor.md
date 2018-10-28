---
title: new 和构造函数
---

```javascript
function Human(options){


}

Human.prototype.______ = ___________ 
Human.prototype.______ = ___________ 
Human.prototype.______ = ___________ 

var human = new Human({name:'Frank', city: 'Hangzhou'})
var human2 = new Human({name:'Jack', city: 'Hangzhou'})
```

补全代码，使得 human 对象满足以下条件：

1. human 这个对象本身具有属性 name 和 city

2. `human.__proto__` 对应的对象（也就是原型）具有物种（species）、走（walk）和使用工具（useTools）这几个属性

3. `human.__proto__.constructor === Human` 为 true

4. human2 和 human 类似。

方法一：

```javascript
function Human(options){
    this.name = options.name
    this.city = options.city
}

Human.prototype.species = 'Human' 
Human.prototype.walk = function(){}
Human.prototype.useTools = function(){}

var human = new Human({name:'Frank', city: 'Hangzhou'})
var human2 = new Human({name:'Jack', city: 'Hangzhou'})
```

方法二：

```javascript
function Human(options){
    this.name = options['name']
    this.city = options['city']
}

Human.prototype.species = 'Human' 
Human.prototype.walk = function(){}
Human.prototype.useTools = function(){}

var human = new Human({name:'Frank', city: 'Hangzhou'})
var human2 = new Human({name:'Jack', city: 'Hangzhou'})
```

方法三：

```javascript
function Human({name,city}){
    this.name = name
    this.city = city
}

Human.prototype.species =  'mankind'
Human.prototype.walk =  'by feet'
Human.prototype.useTools =  'by hands'

var human = new Human({name:'Frank', city: 'Hangzhou'})
var human2 = new Human({name:'Jack', city: 'Hangzhou'})
```

方法四：

```javascript
function Human(name,city){
    this.name = name
    this.city = city
}

Human.prototype.species =  'mankind'
Human.prototype.walk =  'by feet'
Human.prototype.useTools =  'by hands'

var human = new Human('Frank', 'Hangzhou')
var human2 = new Human('Jack', 'Hangzhou')
```