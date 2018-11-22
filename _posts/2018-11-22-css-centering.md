---
title: CSS 居中
---

## flex 布局居中

主流方式，广泛用于pc端和移动端

```css
.container {
    display: flex;
    align-items: center;
    justify-content: center;
}
```

## grid 布局居中

非主流，未来可能取代flex的用法，兼容性待提高

```css
.container {
    display: grid;
    align-items: center;
    justify-content: center;
}
```

## display: table-cell

传统中较新的方法

```css
.container {
    display: table-cell;
    vertical-align: middle;
}
```

## 绝对定位

适用于使用绝对定位的场景，传统方法

```css
.container {
    position: relative;
}
.child {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
```

transform: translate 可以改为负 margin。

```css
.container {
    position: relative;
}
.child {
    position: absolute;
    top: 50%;
    left: 50%;
    margin-left: -50px; /*.child 宽度的一般，假设 .child 宽度为100px*/
    margin-top: -50px; /*.child 高度的一般，假设 .child 高度为100px*/
}
```

```css
.container {
    position:relative;
}
.child {
    position:absolute;
    left:0; 
    right:0; 
    top:0; 
    bottom:0;
    margin:auto;
}
```

## 奇葩方法

利用 vertical-align 的特性实现垂直居中

```css
.container {
    width: 200px;
    height: 200px;
    border: 1px solid red;
}

.container::before {
    content: '';
    display: inline-block;
    width: 0;
    height: 100%;
    vertical-align: middle;
}
```

vertical-align 只对行级元素和 table-cell 生效

## 简单方法

```css
.container {
    padding: 10px 40px;
}
```

## 单行文本固定高度垂直居中

```css
.header {
    line-height: 50px;
}
```

## 水平居中

块级元素，设置固定宽度，左右 margin 等于 auto

```css
div {
    width: 600px;
    margin: 0 auto;
}
```

## 行级元素居中

对块级的父级使用，能让内部的匿名行盒（文字）、行内元素（span）、inline-block 元素在父亲里水平居中

```css
.container {
    text-align: center;
}
```