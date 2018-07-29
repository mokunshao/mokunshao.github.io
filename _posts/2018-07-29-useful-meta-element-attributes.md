---
title: 一些有用的 Meta 元素属性
---

`<Meta>`  元素有很多有用的属性，这篇文章将展示其中一些。

```
<!-- 每五秒刷新一次页面 -->
<meta http-equiv="refresh" content="5">
```

```
<!-- 一打开网页就自动跳转到 https://www.example.com -->
<meta http-equiv="refresh" content="0; url=https://www.example.com">
```

```
<!-- 不让百度转码 -->
<meta http-equiv="Cache-Control" content="no-siteapp" />
```

```
<!-- 阻止所有爬虫 -->
<meta name="robots" content="noindex"> 
```