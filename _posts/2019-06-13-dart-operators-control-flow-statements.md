---
title: Dart 运算符和控制语句
---

### 算术运算符

加减乘除 `+` `-` `*` `/` `~/` `%`

递增递减 `++var` `var++` `--var` `var--`

### 关系运算符

运算符 `==` `!=` `>` `<` `>=` `<=`

判断内容是否相等 `==`

### 逻辑运算符

运算符 `!` `&&` `||`

### 赋值运算符

运算符 `=` `??=`

复合运算符 `+=` `-=` `*=` `/=` `%=` `~/=`

`??=` 在变量没赋值时才赋值（其他语言没有）

### 条件表达式

三目运算符 `condition ? expr1 : expr2`

??运算符 `expr1 ?? expr2` expr1 为空取 expr2（其他语言没有）

### if 语句

`if` `if...elseif` `if...elseif...else`

### for 语句

`for` `for...in`

### whiele 语句

`while` `do...while`

### break 和 continue

`break` `continue`

### switch...case 语句

比较类型：num，string，编译期常量，对象，枚举

非空 case 必须有一个 break

default 处理默认情况

continue 跳转标签（其他语言没有）