---
title: 逻辑运算符
---

`a || b` 和 `a && b` 的值得基本上不能是 true/false，

## && 运算符

`&&` 的意思是“和”

找 falsy 值

有一个假就是假

返回第一个 falsy 值

```javascript
0 && 1 // 0
```

```javascript
1 && 2 && 0 && 3 // 0
```

没有falsy值的话返回最后一个 truthy 值

```javascript
1 && 2 && 4 && 3 // 3
```

a = a || {} 是什么意思

## || 运算符

`||` 的意思是“或”

找 truthy 值

有一个真就是真

返回第一个 truthy 值

```javascript
0 || undefined || null || 1 || 2 || null // 1
```

```javascript
var a = b || {}

// 的意思是

if(b){
    a = b;
}else{
    a = {};
}
```

## ! 运算符

`!` 运算符可以把 truthy 值变成 `false`，把 falsy 值变成 `true`。