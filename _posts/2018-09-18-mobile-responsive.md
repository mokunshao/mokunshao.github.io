---
title: 移动端页面的做法
---

响应式页面可以通过 media query（媒体查询）来对不同宽度页面调用不同的样式。我们要学会针对不同宽度的设备隐藏元素。

我们也可以为不同 User Agent 提供不同的内容，使得手机用户与电脑用户看到不一样的内容。

手机端要加一个 meta：

```html
<meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
```

手机端的交互方式不一样：

- 没有 hover

- 有 touch 事件（但没有滑动事件）

- 没有 resize

- 没有滚动条