---
title: 一些常用的传统布局和居中方法
---

## 常见的左右布局方法

左右布局通常是一列自适应，一列固定宽度。

如何实现：浮动 + `margin-left` 或 `margin-right`

可以两列都浮动，但是如果要想只浮动一列的话，一定要把浮动的那一列写在另一列的前面。

[https://codepen.io/mokunshao/pen/rrdpdE](https://codepen.io/mokunshao/pen/rrdpdE)

<p data-height="265" data-theme-id="dark" data-slug-hash="rrdpdE" data-default-tab="css,result" data-user="mokunshao" data-pen-title="两列布局 左右布局" class="codepen">See the Pen <a href="https://codepen.io/mokunshao/pen/rrdpdE/">两列布局 左右布局</a> by mokunshao (<a href="https://codepen.io/mokunshao">@mokunshao</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

## 常见的左中右布局方法

这个左中右布局的实现方法和上面提到的左右布局一样。

[https://codepen.io/mokunshao/pen/JBLQQz](https://codepen.io/mokunshao/pen/JBLQQz)

<p data-height="265" data-theme-id="0" data-slug-hash="JBLQQz" data-default-tab="css,result" data-user="mokunshao" data-pen-title="左中右布局 三列布局" class="codepen">See the Pen <a href="https://codepen.io/mokunshao/pen/JBLQQz/">左中右布局 三列布局</a> by mokunshao (<a href="https://codepen.io/mokunshao">@mokunshao</a>) on <a href="https://codepen.io">CodePen</a>.</p>

在左中右布局中比较经典的还有圣杯布局和双飞翼布局。

### 1. 圣杯布局

圣杯布局缺点：左边 div 的宽度不能小于中间 div 的宽度，否则页面一缩小就乱掉。

[https://codepen.io/mokunshao/pen/rrvBbj](https://codepen.io/mokunshao/pen/rrvBbj)

<p data-height="265" data-theme-id="0" data-slug-hash="rrvBbj" data-default-tab="css,result" data-user="mokunshao" data-pen-title="圣杯布局" class="codepen">See the Pen <a href="https://codepen.io/mokunshao/pen/rrvBbj/">圣杯布局</a> by mokunshao (<a href="https://codepen.io/mokunshao">@mokunshao</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

### 2. 双飞翼布局

双飞翼布局是对圣杯布局的改进，解决了页面过度缩小后出现的bug。

缺点：多了一个 div，不符合语义化。

[https://codepen.io/mokunshao/pen/mjLeJv](https://codepen.io/mokunshao/pen/mjLeJv)

<p data-height="265" data-theme-id="0" data-slug-hash="mjLeJv" data-default-tab="css,result" data-user="mokunshao" data-pen-title="双飞翼布局" class="codepen">See the Pen <a href="https://codepen.io/mokunshao/pen/mjLeJv/">双飞翼布局</a> by mokunshao (<a href="https://codepen.io/mokunshao">@mokunshao</a>) on <a href="https://codepen.io">CodePen</a>.</p>
<script async src="https://static.codepen.io/assets/embed/ei.js"></script>

## 常见的水平居中方法

1. 若是行内元素, 给其父元素设置 `text-align:center;` 即可实现行内元素水平居中。

2. 若是块级元素, 该元素 `margin-left` 和 `margin-right` 设置为 `auto` 即可。

## 常见的垂直居中方法

1. 若元素是单行文本, 则可设置 `line-height` 等于父元素高度。

2. 若元素是行内块级元素, 可以使用 `display: inline-block;` 来搭配 `vertical-align: middle;`。

3. 行内元素可以设置 `padding-top` 和 `padding-bottom` 为相同的值。

4. `display:table-cell` 搭配 `vertical-align: middle`。