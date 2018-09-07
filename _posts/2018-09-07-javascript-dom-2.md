---
title: DOM 学习笔记二
---

DOM 树的根节点是 html。

## innerText 与 textContent

textContent 是标签中所有的文字。

innerText 是标签中最后显示出来的文字。

textContent 是“代码”中的文字，innerText 只提取最后渲染出来的文字。也就是哪怕用文字在`<script>`标签中 textContent 依然会提取，而 innerText 甚至不会提取 `display: none` 元素里的文字，因为那个元素最后并不显示。

## isEqualNode 与 isSameNode

isEqualNode 检查两个 Node 是否长得一模一样。

isSameNode 检查两个 Node 是否本身就是一个 Node。

## normalize
 
normalize 合并相邻的 Text 并清除空 Text

## cloneNode

cloneNode 的参数为 true 时为深复制，否则为浅复制。

## HTMLCollection 与 NodeList

两者都是动态集合，都是类数组对象。

HTMLCollection 实例对象的成员只能是 Element 节点，NodeList 实例对象的成员可以包含其他节点。

HTMLCollection 实例对象可以用id属性或 name 属性引用节点元素，NodeList 只能使用数字索引引用。

两者少部分方法不一样，比如 NodeList 有 forEach 方法，而 HTMLCollection 没有。

大多数情况下，NodeList 对象都是个实时集合。在另一些情况下，NodeList 是一个静态集合。

```javascript
var parent = document.getElementById('parent');
parent.childNodes.length // 2
parent.appendChild(document.createElement('div'));
parent.childNodes.length // 3

var allDiv = document.querySelectorAll('div')
allDiv.length // 假设是 2
document.body.appendChild(  document.createElement('div')  )
allDiv.length // 2
```

parent.childNodes 是动态集合。所谓动态集合就是一个活的集合，DOM 树删除或新增一个相关节点，都会立刻反映在 NodeList 接口之中。

document.querySelectorAll 方法返回的是一个静态集合。DOM 内部的变化，并不会实时反映在该方法的返回结果之中。