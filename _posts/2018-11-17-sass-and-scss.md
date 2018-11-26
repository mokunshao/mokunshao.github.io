---
title: Sass 与 SCSS
---

Sass 和 SCSS 是同一个语言。

Sass 和 SCSS 的区别是有没有花括号，前者没有，后者有。

npm 上有两个关于 Sass 的包：分别是 Sass 和 node-Sass ，使用前者就行了。

在网页实时编写和编译 Sass：[http://www.Sassmeister.com](http://www.Sassmeister.com)

## 变量 Variables

定义的变量名前要加上美元符号。

```scss
$title-font: normal 24px/1.5 'Open Sans', sans-serif;
$cool-red: #F44336;

h1.title {
  font: $title-font;
  color: $cool-red;
}
```

## 混合 Mixins

@mixins 与 @include 搭配使用。

```scss
@mixin square($size, $color) {
  width: $size;
  height: $size;
  background-color: $color;
}

.blue-square {
  @include square(20px, rgb(0,0,255));
}
```

## 继承

使用 @extend 可以实现继承，将一个选择器的 CSS 属性继承到另一个。

从编译结果看，@extend 比 @include 要省代码。

```scss
%dialog-button {
  box-sizing: border-box;
  color: #ffffff;
  box-shadow: 0 1px 1px 0 rgba(0, 0, 0, 0.12);
  padding: 12px 40px;
  cursor: pointer;
}

.confirm {
  @extend %dialog-button;
  background-color: #87bae1;
  float: left;
}
```

## 嵌套

```scss
nav {
  ul {
    margin: 0;
    padding: 0;
    list-style: none;
  }

  li { display: inline-block; }

  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```

## Import

使用 @import 引入其他 .Sass 或 .SCSS 文件

```scss
@import 'reset';

body {
  font: 100% Helvetica, sans-serif;
  background-color: #efefef;
}
```

## 运算符

可以使用 `+`，`-`，`*`，`/`，`%` 运算符。

```scss
aside{
  width: 300px / 960px * 100%;
}
```

## 函数

Sass 提供很多有用的内置函数，常见的有 `darken()` 和 `lighten()`。

```scss
body{
    background: darken(#800, 20%);
}
```

你也可以编写自己的函数。

```scss
@function function-name($args) {  
 @return value-to-be-returned;  
}
```