---
title: 一个布局原则和两个布局套路
---

## 原则

不到万不得已，不要写死 width 和 height。

尽量用高级语法，如 calc、flex。

如果是 IE，就全部写死。

## 消除元素间的空隙

方案一：

父元素加 `display: flex;`

方案二：

使用 `float:left;` 或者 `float:right;`

## space-between 的效果

方案一：

父元素加 `display: flex;`

父元素加 `justify-content: space-between;`

方案二：

给子元素设置 `float:left;`

给子元素左右设置一样的 margin。

如果宽度不够，可以给父元素添加左右负 margin。

## flex 的魔法

默认情况下，父元素 `display:flex;` 会使子元素都向左边挤在一起。

这时给其中一个子元素添加 `margin-left:auto;` 会跑到最右。