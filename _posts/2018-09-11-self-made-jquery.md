---
title: 自制简易 jQuery
---

## 需求

```
window.jQuery = ???
window.$ = jQuery // 给个缩写

var $div = $('div') 
$div.addClass('red') // 可将所有 div 的 class 添加一个 red
$div.setText('hi') // 可将所有 div 的 textContent 变为 hi
```

## 成品

源码：[https://github.com/mokunshao/Self-made-jQuery/blob/master/index.html](https://github.com/mokunshao/Self-made-jQuery/blob/master/index.html)

Demo：[https://mokunshao.github.io/Self-made-jQuery/index.html](https://mokunshao.github.io/Self-made-jQuery/index.html)

## 思路

jQuery 类似一个封装好的函数，提供给我们各种方法，同样的需求下，使用 jQuery 让开发者少敲很多代码并且解决不同浏览器兼容性的问题。

### 1. 封装函数

```javascript
function getSiblings(node){
    // write some code...
}
```

### 2. 命名空间

命名空间可以防止污染全局变量。

```javascript
var jQuery = {}
jQuery.getSiblings = function(node){ // write some code...}
jQuery.setText = function(node){ // write some code...}

// 调用函数时
jQuery.getSiblings(node)
jQuery.setText(node)
```

### 3. 把 node 提前

效果：

```javascript
// 调用函数时
node.getSiblings()
$node.getSiblings()
```

jQuery 的属性和方法保存于 jQuery.prototype。不过这里不采用这种方法。

方法一：扩展 Node 接口。直接在 Node.prototype 上加函数。可能的风险是覆盖原生的属性和方法。

```javascript
Node.prototype.getSiblings = function(){
    // write some code...
}
```

方法二：添加新的接口。第二种叫做「无侵入」。

```javascript
window.jQuery = function(nodeOrSelector) {
  let nodes = {
    0: nodeOrSelector,
    length: 1
  }
  nodes.addClass = function(classes) {}
  nodes.text = function(text) {}
  return nodes
}

var node2 = jQuery('ul > li')
// 调用函数时
node2.addClass(['blue'])
```