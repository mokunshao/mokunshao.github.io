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

1. 定位元素（z-index为0及以上或者auto）

2. 内联元素（含inline-block元素）

3. 浮动元素

4. 块级元素

1. 定位元素（z-index 为负数 父元素被定位且z-index 不为auto）

5. border

6. background

1. 定位元素（z-index 为负数 且父元素没有被定位）

## 堆叠上下文

可以理解为堆叠作用域。跟 BFC 一样，我们只知道一些属性会触发堆叠上下文，但并不知道堆叠上下文是什么。

[https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Understanding_z_index/The_stacking_context](https://developer.mozilla.org/zh-CN/docs/Web/Guide/CSS/Understanding_z_index/The_stacking_context)

## z-index

z-index 属性设置元素的堆叠顺序。拥有更高堆叠顺序的元素总是会处于堆叠顺序较低的元素的前面。

[https://cssreference.io/property/z-index/](https://cssreference.io/property/z-index/)