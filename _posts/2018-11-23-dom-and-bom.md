---
title: DOM 与 BOM
---

## DOM

DOM 是 Document Object Model。

DOM 描述了处理网页内容的方法和接口。

DOM 是 W3C 标准。

DOM 代表着被加载到浏览器窗口里的当前网页。

DOM的最根本对象是 document（window.document）。

Document 根节点包含子节点：forms、location、anchors、images、links 等。

从 window.document 可以看出，DOM 的最根本的对象是 BOM 的 window 对象的子对象。

## BOM

BOM 是 Browser Object Model。

BOM 描述了与浏览器进行交互的方法和接口。

BOM 没有相关标准。

window 对象：BOM 的核心是 window，而 window 对象又具有双重角色，它既是通过 js 访问浏览器窗口的一个接口，又是一个 global（全局）对象。这意味着在网页中定义的任何对象，变量和函数，都以 window 作为其 global 对象。

Window 对象包含属性：document、location、navigator、screen、history、frames 等。

document 对象：实际上是 window 对象的属性，document === window.document 为 true，是唯一一个既属于 BOM 又属于 DOM 的对象。

location 对象：表示载入窗口的URL，也可用 window.location 引用它。

screen 对象：用于获取某些关于用户屏幕的信息，也可用 window.screen 引用它。  