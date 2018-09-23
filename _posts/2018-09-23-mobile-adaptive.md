---
title: 移动端是怎么做适配的？
---

## meta viewport

默认情况下在移动端浏览器会把viewport的宽度设置为980px，然后把所有内容按比例缩小后硬塞进小的显示屏里。

在 head 元素内添加以下代码即可解决以上问题：

```html
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
```

## 媒体查询

我们可以针对不同的屏幕宽度的设备设置不同的 css，借助媒体查询在不同屏幕宽度的设备调用不同的样式。

```html
<!-- link元素中的CSS媒体查询 -->
<link rel="stylesheet" media="(max-width: 800px)" href="example.css" />

<!-- 样式表中的CSS媒体查询 -->
<style>
@media (max-width: 600px) {
  .sidebar {
    display: none;
  }
}
</style>
```

## 动态 rem 方案

### 使用 js 动态调整 rem

通过以下两种方法可以给不同宽度的设备设置不同的 1rem 的值。

方法一：

缺点：无法随着页面宽度的变化而变化。

```javascript
let pageWidth = window.innerWidth  
document.write('<style>html{font-size:'+pageWidth/10+'px;}</style>')
```

方法二：

优点：可以随着页面宽度的变化而变化。

```javascript
let pageWidth = window.innerWidth;
let html =document.getElementsByTagName('html')[0];

function setRem(){
    pageWidth = window.innerWidth;
    html.style.fontSize = pageWidth/10+'px';
}

setRem()

window.onresize = function(){
    setRem()
}
```

### 使用 css 动态调整 rem

用媒体查询的方法改变 html 的 font-size，从而改变 1rem 的值。

```css
html {
    font-size: 16px;
}

@media screen and (max-width: 320px){
    html {
        font-size: 13.65px !important;
    }
}

@media screen and (min-width: 376px) and (max-width: 414px){
    html {
        font-size: 17.66px !important;
    }
}

@media screen and (min-width: 415px) and (max-width: 768px){
    html {
        font-size: 32.76px !important;
    }
}

@media screen and (min-width: 769px) and (max-width: 1024px) {
    html{
        font-size: 43.69px !important;
    }
}
```

## 使用 jQuery 动态调整 rem

```javascript
let pageWidth
let oneRem

function setFont() { 
  pageWidth= window.innerWidth; 
  oneRem = pageWidth/10; 
  $('html').css('font-size',oneRem); 
}

setFont(); 

$(window).on('resize', function () { 
  setFont(); 
})
```