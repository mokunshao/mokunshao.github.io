---
title: CSS 宽度和高度
---

内联元素的高度由字体及行高决定，宽度由内容、`padding`、`border` 和 `margin` 决定。

块级元素的宽度自适应父元素，高度由其内部文档流元素的高度总和决定。若有脱离文档流的则不计算它的高度。

文档流中内联元素默认从左到右排列，宽度不够则自动换行。

文档流中块级元素从上到下排列，每个元素占一行。

空格的宽度由设计师决定。

元素之间无论多少个空格和回车都显示为一个空格。

使用 `&nbsp;` 可以实现多个空格。

`word-break:break-all;` 可以给长单词换行。

每个字体的建议行高由于字体设计师设计，但我们可以使用 `line-height` 属性改变。

一个子元素脱离文档流后计算父元素高度不再算它的高度，脱离文档流的方式：`float：left；` ，`position：absolute；` ，`position：fixed;`。

相对定位 `position: relative;` 不脱离文档流，不管位置怎样移动，父元素计算高度仍要算上它的高度。

不要用 `height` 设置高度，容易出 Bug。设置高度的话要设置 `padding-top` 和 `padding-bottom`。

##阻止 margin 合并的方法

这里研究的情况是一个块级元素内包含一个块级元素。

阻止 `margin` 合并可以在设置父元素的上下方向的 `padding` 或者上下方向的 `border`  或者 `overflow:hidden;`。

## 两种居中方法

这里研究的情况是一个块级元素内包含一个块级元素，要居中的是内部的块级元素，实现上下左右方向的居中。

父元素设置 `adding-top` 和 `padding-bottom` ，子元素设置 `margin-left` 和 `margin-right` 为 `auto`。

使用 flex 的居中方法为 `display: flex;　justify-content:center;　align-items:center;`