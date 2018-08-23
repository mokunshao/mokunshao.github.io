---
title: CSS 的难点与套路
---

## 难点

CSS 的难就难在它的不正交，不同属性有时候会相互影响。

1. `border` 影响 `margin` 合并

上下方向的相邻元素会出现 `margin` 合并的情况，这时候如果两者的之间有个空白的 `div` 元素，这个 `div` 元素没有 `height`、`margin` 以及 `padding`，只是设置 `border-top` 或者 `border-bottom`，即可化解 `margin` 合并。或者设置该 `div` 为 `display: table` 或者 `display: flex`

父子元素之间的 `margin` 合并的解决方法，可以给父元素添加`display:flex` 、`display: table` 、`overflow: hidden`或者添加上下方向的 `padding` 和 `border`

2. 给 `li` 元素设置 `display: block` 的话，`li` 自带的 list-style 就不见了。`display: inline` 、 `display: inline-block` 、 `display: flex` ，`display: table` 一样会出现这种情况。

3. `position: absolute` 影响 `display: inline`  和 `display: inline-block` 的元素。对某元素使用 `position: absolute` 后 ，该元素由原本的 `display: inline`  或者 `display: inline-block`
转变为 `display: block` 的元素。

4. `transform` 影响 `position` ：如果子元素为 `position:fixed` 如果父元素使用了`transform` 属性，例如 `transform: scale(1.1)` 则子元素相对于父元素进行固定定位，而不是之前的效果。

5. `flow` 元素影响 `inline` 元素， `inline` 元素里的文字似乎能够感知到 `flow` 元素，不会被 `flow` 元素遮挡文字。

## 套路

float 布局和 flex 布局可以胜任绝大部分的情况。

float 对 IE 兼容好，flex 兼容手机浏览器、现代的浏览器。

### 水平居中的套路

对于 block 元素：

child 宽度不确定：左右方向 `margin` 给一个确定数值。

child 宽度确定：左右方向的 `margin` 为 `auto`。

对于 inline 元素：parent 设置 `text-align:center`，child 设置 `display:inline` 或者 `display:inline-block`。

### 垂直居中的套路

child 高度确定以及不确定：设置 `padding-top`，`padding-bottom`。

parent 高度确定：table 布局 和 flex 布局可以胜任绝大部分的情况。IE 使用 table 或者用 div 模拟 table。flex 兼容手机浏览器、现代的浏览器。