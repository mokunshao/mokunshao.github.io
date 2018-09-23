---
title: 写一个符合规范的 HTML 文件
---

请写出一个符合 W3C 规范的 HTML 文件，要求:

1. 页面标题为「我的页面」

2. 页面中引入了一个外部 CSS 文件，文件路径为 /style.css

3. 页面中引入了另一个外部 CSS 文件，路径为 /print.css，该文件仅在打印时生效

4. 页面中引入了另一个外部 CSS 文件，路径为 /mobile.css，该文件仅在设备宽度小于 500 像素时生效

5. 页面中引入了一个外部 JS 文件，路径为 /main.js

6. 页面中引入了一个外部 JS 文件，路径为 /gbk.js，文件编码为 GBK

7. 页面中有一个 SVG 标签，SVG 里面有一个直径为 100 像素的圆圈，颜色随意

8. 注意题目中的路径

```html
<!DOCTYPE html>
<html>
<head>
    <title>我的页面</title>
    <link rel="stylesheet" type="text/css" href="./style.css">
    <link rel="stylesheet" type="text/css" href="./print.css" media="print">
    <link rel="stylesheet" type="text/css" href="./mobile.css" media="(max-width:500px)">
</head>
<body>
    <svg height="500" width="500">
        <circle cx="100" cy="100" r="50" stroke="black" stroke-width="2" fill="red"/>
    </svg>
    <script type="text/javascript" src="./main.js"></script>
    <script type="text/javascript" src="./gbk.js" charset="GBK"></script>
</body>
</html>
```