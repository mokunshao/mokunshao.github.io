---
title: CSS 堆叠上下文
---

## 堆叠顺序

border 比 background 更靠近用户，遮住 background 的一部分。

文字比 border 更靠近用户。

内联元素比块级元素离用户更近。

同样是文字，子元素的文字比父元素的文字离用户更近。

同级元素，后出现者比前出现者更靠近用户。

元素从上到下排序：

1. 定位元素

2. 内联元素（含inline-block元素）

3. 浮动元素

4. 块级元素

5. border

6. background

## 堆叠上下文

[https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Understanding_z_index/The_stacking_context](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Understanding_z_index/The_stacking_context)
