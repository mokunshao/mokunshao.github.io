---
title: JavaScript 的数据类型转换
---

## 任意类型转字符串

### String(x)

该方法可用于任何类型的数字，字母，变量，表达式。

```javascript
String(1)
// "1"
String(true) 
// "true"
String(null) 
// "null"
String(undefined) 
// "undefined"
String({}) 
// "[object Object]"
```

### x.toString()

除了 `null` 和 `undefined` 之外，其他的类型（数值，布尔，字符串，对象）都有此方法，它返回相应值的字符串表现(并不修改原变量)。

```javascript
(1).toString()
// "1"
true.toString()
// "true"
null.toString()
// Uncaught TypeError: Cannot read property 'toString' of null
    at <anonymous>:1:6
undefined.toString()
// Uncaught TypeError: Cannot read property 'toString' of undefined
    at <anonymous>:1:11
{}.toString()
// "[object Object]"
```

### x + ''

使用加法运算符配合一个空字符串可以把任意值转换为字符串。

```javascript
1 + ''
// '1'
true + ''
// 'true'
null + ''
// 'null'
undefined + ''
// 'undefined'
{} + ''
// 0
var o ={}
o + ''
// [object Object]
```

## 任意类型转数字

Number(x)

使用 Number() 函数，可以将任意类型的值转化成数值。

```javascript
Number("123")
// 123
Number('324abc') 
// NaN
Number('') 
// 0
Number(true)
// 1
Number(false)     
//  0
Number(null)
// 0
Number(undefined)
// NaN
Number({})
// NaN
```

parseInt(x, 10)

parseInt() 函数可解析一个字符串，并返回一个整数。

```javascript
parseInt(null, 10)
// NaN
parseInt(undefined, 10)
// NaN
parseInt("a", 10)
// NaN
parseInt("123", 10)
// 123
parseInt("123.123", 10)
// 123
parseInt(true, 10)
// NaN
parseInt({}, 10)
// NaN
```

parseFloat(x)

parseFloat() 函数可解析一个字符串，并返回一个浮点数。

```javascript
parseFloat(null)
// NaN
parseFloat(undefined)
// NaN
parseFloat("123")
// 123
parseFloat("123.123")
// 123.123
parseFloat({})
// NaN
parseFloat(true)
// NaN
```

x - 0

```javascript
'1'-0
// 1
null-0
// 0
undefined-0
// NaN
{}-0
// -0
true-0
// 1
false-0
// 0
'10.5'-0
// 10.5
```

+x

```javascript
+true
// 1
+false
// 0
+'100.5'
// 100.5
+{}
// NaN
+null
// 0
+undefined
// NaN
```

x/1

```javascript
2/1
// 2
'2.5'/1
// 2.5
undefined/1
// NaN
null/1
// 0
({})/1
// NaN
```
x\*1
```javascript
2*1
// 2
'2.5'*1
// 2.5
undefined*1
// NaN
null*1
// 0
({})*1
// NaN
```



## 任意类型转布尔

Boolean(x)

Boolean 函数可以将任意类型的值转为布尔值。

```javascript
Boolean('x')
// true
Boolean(null)
// false
Boolean(undefined)
// false
Boolean(0)
// false
Boolean(2)
// true
Boolean({})
// true
Boolean(NaN) 
// false
Boolean('') 
// false
```

!!x

```javascript
!!1
// true
!!0
// false
!!‘1’
// true
!!null
// false
!!undefined
// false
!!{}
// true
```


## Falsy

falsy 是在 Boolean 上下文中认定可转换为 `false` 的值。

使用 Boolean() 方法可以强制转换任意值为 boolean 类型,除了以下几个值，其他都是自动转为 `true`：

- `false`

- `null`

- `undefined`

- `0`

- `NaN`

- `''`

- `""`

- `document.all`