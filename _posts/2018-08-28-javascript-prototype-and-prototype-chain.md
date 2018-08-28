---
title: JavaScript 的原型与原型链
---

原型（prototype）是一次性给一堆对象添加属性和方法的对象。

我们把由原型组成的链式结构称为原型链（prototype chain）。

## 请注意

所有的对象都有 `__proto__` 属性，该属性对应该对象的原型；

所有的函数对象都有 `prototype` 属性，该属性的值会被赋值给该函数创建的对象的 `__proto__` 属性；

所有的对象可以通过不断使用 `__proto__` 属性找到 `Object.prototype` ；

所有的原型对象都有 `constructor` 属性，该属性对应创建所有指向该原型的实例对象的构造函数；

函数对象和原型对象通过 `prototype` 和 `constructor` 属性进行相互关联。

## 通俗地讲

我们所创建的每一个函数，解析器都会向函数中添加一个属性 `prototype`。

这个属性对应着一个对象，这个对象就是我们所谓的原型对象。

如果函数作为普通函数调用 `prototype` 没有任何作用。

当函数以构造函数的形式调用时，它所创建的对象都会有一个隐含的属性，指向该构造函数的原型对象，我们可以通过 `__proto__` 来访问该属性。

原型对象就相当于一个公共的区域，所有同一个类的实例都可以访问到这个原型对象，我们可以将对象中共有的内容，统一设置到对象中。

当我们访问一个对象的属性或方法时，它会先在对象自身寻找，如果有则直接使用，如果没有则会去原型对象中寻找，如果找到则直接使用。

以后我们创建构造函数时，可以将这些对象共有的属性和方法，统一添加到构造函数的原型对象中，这样不用分别为每一个对象添加，也不会影响到全局作用域，就可以使每个对象都具有这些属性和方法了。

使用 `in` 检查对象中是否含有某个属性时，如果对象中没有但是原型中有，也会返回 `true`。

```javascript
console.log('name' in mc)
```

可以使用对象的 `hasOwnProperty()` 来检查对象自身是否含有该属性，使用该方法时只有对象自身中含有属性时，才会返回 `true`。

```javascript
console.log(mc.hasOwnProperty('name'))
```

原型对象也是对象，所以它也有原型。

当我们使用一个对象的属性或方法时，会先在自身中寻找，自身中如果有，则直接使用，如果没有则去原型对象中寻找，如果原型对象中有，则使用，如果没有则去原型的原型中寻找，直到找到 `Object` 对象的原型，`Object` 对象的原型没有原型，如果在 `Object` 中依然没有找到，则返回 `undefined`。

## 相关公式

```javascript
var 对象 = new 函数()
对象.__proto__ === 对象的构造函数.prototype

// 推论
var number = new Number()
number.__proto__ === Number.prototype
Number.__proto__ === Function.prototype // 因为 Number 是 Function 的实例

var object = new Object()
object.__proto__ === Object.prototype
Object.__proto__ === Function.prototype // 因为 Object 是 Function 的实例

var function = new Function()
function.__proto__ === Function.prototype
Function.__proto__ === Function.prototye // 因为 Function 是 Function 的实例！
```

```javascript
Object.prototype.__proto__ === null
Number.prototype.__proto__.__proto__ === null
Function.prototype.__proto__.__proto__ === null
String.prototype.__proto__.__proto__ === null
```

```javascript
Number.prototype.__proto__ === Object.prototype
String.prototype.__proto__ === Object.prototype
Function.prototype.__proto__ === Object.prototype
```