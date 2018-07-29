---
title: 五种 HTML 元素类型 
---

本文简单讲解了空元素、可替换元素、不可替代元素、行内元素、块状元素。

<!-- more -->

## 1. 空元素

在 HTML 元素中，没有内容的 HTML 元素被称为空元素（empty element）。通常在一个空元素上使用一个闭标签是无效的。

空元素列表：[https://developer.mozilla.org/en-US/docs/Glossary/Empty_element](https://developer.mozilla.org/en-US/docs/Glossary/Empty_element)



## 2. 可替换元素 & 不可替代元素

可替换元素（replaced element）就是浏览器根据元素的标签和属性，来决定元素的具体显示内容。可替换元素的展现不是由CSS来控制的。可替换元素通常为空元素。

可替换元素列表：[https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element](https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element)

HTML 的大多数元素是不可替换元素，他们将内容直接告诉浏览器，将其显示出来。 


## 3. 行内元素 & 块级元素

块级元素（block-level elements）在浏览器上表现为占据整行，不与其他元素共在同一行。可以在内嵌套块级元素和行内元素。

行内元素（inline elements）则与其他行内元素可以共同位于同一行。行内元素内部也可以嵌套其他元素，但是不能是块级元素。

行内元素列表：[https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements)

块状元素列表：[https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)