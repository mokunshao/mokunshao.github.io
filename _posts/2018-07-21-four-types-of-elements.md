---
title: 四种元素 
---

本文简单讲解了空元素、可替换元素、行内元素、块状元素。

<!-- more -->

## 1. 空元素

在 HTML 元素中，没有内容的 HTML 元素被称为空元素（empty element）。通常在一个空元素上使用一个闭标签是无效的。

空元素列表：[https://developer.mozilla.org/en-US/docs/Glossary/Empty_element](https://developer.mozilla.org/en-US/docs/Glossary/Empty_element)

> 参考资料：
>
> [http://www.runoob.com/html/html-elements.html](http://www.runoob.com/html/html-elements.html)
>
> [https://developer.mozilla.org/en-US/docs/Glossary/Empty_element](https://developer.mozilla.org/en-US/docs/Glossary/Empty_element)


## 2. 可替换元素

可替换元素（replaced element）就是浏览器根据元素的标签和属性，来决定元素的具体显示内容。可替换元素的展现不是由CSS来控制的。可替换元素通常为空元素。

可替换元素列表：[https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element](https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element)

> 参考资料：
>
> [https://www.jianshu.com/p/2524609fab2f](https://www.jianshu.com/p/2524609fab2f)
>
> [https://www.jb51.net/css/74447.html](https://www.jb51.net/css/74447.html)
>
> [https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element](https://developer.mozilla.org/en-US/docs/Web/CSS/Replaced_element)

## 3. 行内元素 & 块级元素

HTML 元素大多数都是行内元素或块级元素。

块级元素（block-level elements）在浏览器上表现为占据整行，不与其他元素共在同一行。可以在内嵌套块级元素和行内元素。

块级元素占据其父元素（容器）的整个空间，因此创建了一个“块”。通常浏览器会在块级元素前后另起一个新行。

行内元素（inline elements）则与其他行内元素可以共同位于同一行。行内元素内部也可以嵌套其他元素，但是不能是块级元素。

一般情况下，行内元素只能包含数据和其他行内元素。

一个行内元素只占据它对应标签的边框所包含的空间。而块级元素可以包含行内元素和其他块级元素。这种结构上的包含继承区别可以使块级元素创建比行内元素更”大型“的结构。

默认情况下，行内元素不会以新行开始，而块级元素会新起一行。

行内元素列表：[https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements)

块状元素列表：[https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)

> 参考资料：
>
> [https://developer.mozilla.org/zh-CN/docs/Web/HTML/Inline_elemente](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Inline_elemente)
>
> [https://developer.mozilla.org/zh-CN/docs/Web/HTML/Block-level_elements](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Block-level_elements)
>
> [https://cloud.tencent.com/developer/article/1133352](https://cloud.tencent.com/developer/article/1133352)
>
> [https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Inline_elements)
>
> [https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements](https://developer.mozilla.org/en-US/docs/Web/HTML/Block-level_elements)