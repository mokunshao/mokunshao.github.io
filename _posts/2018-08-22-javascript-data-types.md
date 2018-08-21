---
title: JavaScript 数据类型
---

JavaScript 有7种数据类型: `Number`、`String`、`Boolean`、`Symbol`、`Object`、`null`、`undefined`。

JavaScript 数据类型分为两种：简单数据类型（也称为基本数据类型或者基础数据类型）和复杂数据类型（也叫引用数据类型）。

简单数据类型有：`undefined`、`null`、`Boolean`、`Number` 、`String` 和 `Symbol`。

复杂数据类型有：`Object`。

我们可以用 `typeof` 操作符检测数据类型，这里有一些比较特殊的情况：`null` 返回的是 `object`。`function` 返回的是 `function`，然而并不存在 `function` 类型。

不存在名为数组的数据类型。

这些数据类型都有一系列的方法，也都有一系列互相转化的方法，比如 `parseInt`、`toString`、`Number`、`Boolean`等。

## Number（数值）

Number 的类型及示例：

- 十进制整数：2

- 十进制浮点数：1.1、.1

- 科学记数法：1.23e2

- 二进制：0b11 （有前缀 `0b` 或 `0B` 的数值。）

- 八进制：011、0o11 （有前缀 `0o` 或 `0O` 的数值，或者有前导0、且只用到0-7的八个阿拉伯数字的数值。）

- 十六进制：0x11 （有前缀 `0x` 或 `0X` 的数值。）

- Infinity（无穷,有正负之分。）

- NaN （非数字。）

一些小数计算会有误差，比如 0.1 + 0.2 不等于 0.3。

浮点数值需要的内存空间是保存整数值的两倍。

## String（字符串）

多行字符串：
```javascript
var s = '12345' +
'67890' // 无回车符号

var s = `12345
67890` // 含回车符号

var longString = 'Long \
string' // 不推荐，“\”的后边有其他字符（例如空格）的话会出错
```

引号的里面有引号可以使用转义符：`\'` 或者 `\"`。

ASCII字符可以以 `\x##` 形式的十六进制表示，例如：

```javascript
'\x41'; // 完全等同于 'A'
```

还可以用 `\u####` 表示一个Unicode字符：

```javascript
'\u4e2d\u6587'; // 完全等同于 '中文'
```

## Boolean（布尔值）

只有两个值：`true` 和 `false`。`true` 和 `false` 是区分大小写的。

`Undefined`、`null`、`0`、`NaN`、空字符串，用来判断的话都是 `false`。

下列运算符会返回布尔值：

```
两元逻辑运算符： && (And)，|| (Or)

前置逻辑运算符： ! (Not)

相等运算符：===，!==，==，!=

比较运算符：>，>=，<，<=
```

## null 与 undefined

`null` 和 `undefined` 的区别: `null` 表示一个空值，`undefined` 表示一个值未定义，大多数情况下都应该用 `null`，`undefined` 仅仅在判断函数参数是否传递的情况下有用。

## Object （对象）

对象是一种**无序**的复合数据集合。

建议给键名加引号，否则在不符合标识名的情况下会报错。

`object['key']` 可以写作 `object.key`，前者适用范围更广。

`object['key']` 不等于 `object[key]`。

## Symbol

`Symbol` 用来表示独一无二的值。`Symbol` 值是通过 `Symbol` 函数生成的。