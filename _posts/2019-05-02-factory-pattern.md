---
title: 工厂模式
---

### 介绍

将 new 操作单独封装

遇到 new 时，就要考虑是否该使用工厂模式

简单工厂模式：提供一个创建一系列相关对象的入口，统一了对象创建职责，创建对象无需关心具体类。

工厂模式：提供一个创建一系列相关对象的入口，统一了对象创建职责，创建对象无需关心具体类。使用一个工厂类进行创建。

抽象工厂模式：一个工厂类可以对应多个产品类，对应产生多个实例对象。

### 演示

```javascript
class Product {
  constructor(name) {
    this.name = name;
  }
  init() {
    console.log("init");
  }
  fn1() {
    console.log("fn1");
  }
}

class Creator {
  create(name) {
    return new Product(name);
  }
}

const creator = new Creator();
const p = creator.create("p1");
console.log(p);
p.init();
p.fn1();

```

```javascript
class Student {
  constructor(name, courses) {
    this.name = name;
    this.courses = courses;
  }
}

function factory(name, type) {
  switch (type) {
    case "文科":
      return new Student(name, ["政治", "历史", "地理"]);
    case "理科":
      return new Student(name, ["生物", "物理", "化学"]);
    default:
      throw "没有这个专业，别瞎填";
  }
}

const xm = factory("小明", "文科");
const xh = factory("小红", "理科");

console.log(xm);
console.log(xh);
```

```javascript
function People(name) {
  if (this instanceof People) {
    this.name = name;
  } else {
    return new People(name);
  }
}

const xh = new People("小红");
const xm = People("小明");

console.log(xh);
console.log(xm);
```

### 应用场景

jQuery - $('div')

React.createElement

Vue.js 异步组件