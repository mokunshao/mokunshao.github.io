---
title: 字面量与模板字面量
---

## 字面量

### 字符串字面量

```javascript
let a = 'word'
```

通过内置构造函数生成包装对象：

```javascript
let a = new String('word')
```

### 布尔字面量

```javascript
let a = true
```

通过内置构造函数生成包装对象：

```javascript
let a = new Boolean(true)
```

### 浮点数字面量

```javascript
let a = 3.14
```

通过内置构造函数生成包装对象：

```javascript
let a = new Number(3.14)
```

### 整数

```javascript
let a = 3
```

通过内置构造函数生成包装对象：

```javascript
let a = new Number(3)
```

### RegExp literals

```javascript
let a = /xyz/
```

通过内置构造函数生成：

```javascript
let a = new RegExp('xyz')
```

### 数组字面量

```javascript
let a = [1,2,3]
```

通过内置构造函数生成：

```javascript
let a = new Array(1,2,3)
```

### 对象字面量

```javascript
let a = {b:1}
```

通过内置构造函数生成：

```javascript
let a = new Object({b:1})
```

## 模板字面量

模板字面量（template literals）又称为模板字符串。它包含一些新特征。

```javascript
let a =
`第一行，
第二行，
第三行。`
```

```javascript
let a = `I am ${2+3} years old.`
```

```javascript
let a = `China`
let b = `I live in ${a}.`
```