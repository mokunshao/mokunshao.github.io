---
title: JavaScript 中的 void
---

用于立即执行函数

```javascript
void function iife() {
    console.log(123)
}();
```

用于实现点击后无反应

```html
<a href="javascript:void(0);">超链接</a>
<!-- 去掉 void(0) 也可以实现同样效果 -->
<a href="javascript:;">超链接</a>
```