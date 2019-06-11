---
title: Dart 数据类型
---

main 函数是程序的入口。

```dart
void main(){
	// do something
}
```

print 用来输出内容，类似 JavaScript 的 console.log

使用 var 声明变量，可以赋予不同类型的值。未初始化时，默认值为 null。

使用 final 声明一个只能赋值一次的变量。

使用 const 声明常量，使用const声明的必须是编译期常量。

### 内置类型：

数值型 Number

字符串 String

布尔型 Boolean

列表 List

键值对 Map

Runes

Symbols

### 数值型 num

数值型 num 可以分为：整型 int 和浮点型 double。

```dart
void main(){
	num a = 1;
	int b = 2;
	double c = 3.1;
}
```

运算符 `+` `-` `*` `/` `~/` `%`

特殊的运算符 `~/` 取整

常用属性：isNaN isEven isOdd

常用方法：abs() round() floor() ceil() toInt() toDouble()

### 字符串 String

使用单引号、双引号创建字符。

使用三个单引号或者双引号创建多行字符串。

使用 r 创建原始 raw 字符串

```dart
void main(){
	String a = 'a';
	String b = "b";
	String c = '''c''';
	String c = """c""";
	String d = 'Hello \n World';
	String e = r'Hello \n World';
}
```

运算符：`+` `*` `==` `[]`

插值表达式：`${expression}`

常用属性：length isEmpty isNotEmpty

常用方法：contains() subString() startsWith() endsWith() indexOf() lastIndexOf() toLowerCase() toUpperCase() trim() trimLeft() trimRight() split() replaceXXX()

### 布尔型 bool

```dart
void main(){
	bool a = true;
	bool b = false;
}
```

### 列表 List

List 即数组。

创建 List：`var list = [1,2,3];`

创建不可变的 List：`var list = const [1,2,3];`

构造创建 List：`var list = new List();`

常用操作：[] length add() insert() remove() clear() indexOf() lastIndexOf() sort() sublist() shuffle() asMap() forEach() 

### Map

创建 Map：`var map = {'first':'Dart',2:'Java',true:'2'};`

创建不可变 Map：`var language = const {'first':'Dart','second':'Java'};`

构造创建 List：`var language = new Map();`

常用操作：[] length isEmpty() isNotEmpty() keys values containsKey() containsValue() remove() 

### dynamic

dynamic 即动态类型。

```dart
void main(){
	var a;
	a = 10;
	a = 'dart';

  dynamic b = 20;
  b = 'javascript'

  var list = new List<dynamic>();
  list.add(1);
  list.add('hello');
  list.add(true);
}
```
