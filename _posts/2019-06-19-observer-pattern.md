---
title: 观察者模式
---

```javascript
class Subject {
  constructor(name) {
    this.name = name;
    this.observers = [];
    this.state = "心情好";
  }
  attach(observer) {
    this.observers.push(observer);
  }
  setState(newState) {
    this.state = newState;
    this.observers.forEach(observer => observer.update(this.state));
  }
}

class Observer {
  constructor(name) {
    this.name = name;
  }
  update(state) {
    console.log(`${this.name}知道${state}`);
  }
}

const son = new Subject("小宝宝");
const dad = new Observer("爸爸");
const mom = new Observer("妈妈");

son.attach(dad);
son.attach(mom);

son.setState("心情不好");
son.setState("心情好");
```