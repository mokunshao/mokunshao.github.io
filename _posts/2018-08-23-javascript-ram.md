---
title: JavaScript 内存图
---

操作系统开机即占用 512MB

Chrome 打开即占用 1G 内存

Chrome 各每个网页分配一定数量的内存

这些内存要分给页面渲染器、网络模块、浏览器外壳和 JS 引擎（V8引擎）

JS 引擎将内存分为代码区和数据区

我们只研究数据区

数据区分为 Stack（栈内存） 和 Heap（堆内存）

简单类型的数据直接存在 Stack 里

复杂类型的数据是把 Heap 地址存在 Stack 里

```javascript
var a = 1
var b = a
b = 2
请问 a 显示是几？  
```

a 的值为1

![](https://raw.githubusercontent.com/mokunshao/images/master/javascript-ram-1.png)

```javascript
var a = {name: 'a'}
var b = a
b = {name: 'b'}
请问现在 a.name 是多少？
```

a.name的值为”a“

![](https://raw.githubusercontent.com/mokunshao/images/master/javascript-ram-2.png)

```javascript
var a = {name: 'a'}
var b = a
b.name = 'b'
请问现在 a.name 是多少？
```

a.name的值为“b“

![](https://raw.githubusercontent.com/mokunshao/images/master/javascript-ram-3.png)

```javascript
var a = {name: 'a'}
var b = a
b = null
请问现在 a 是什么？
```

a的值为{name: 'a'}

![](https://raw.githubusercontent.com/mokunshao/images/master/javascript-ram-4.png)