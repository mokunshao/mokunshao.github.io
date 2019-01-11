---
title: CSS in React
---

## 传统方法

直接在 className 上写类名。

或者借助一个名为 classnames 的库写多个类名。

然后在 js 里 import css。

缺点：css 是全局的。

## 借助各种库

- styled-components（推荐）

- emotion

- CSS Modules（推荐）

- radium

开发【普通应用】推荐使用 styled-components 和 CSS Modules，因为类名会变成随机字符串，多人开发也不怕类名重复。

开发【库】应使用传统 CSS 方式，因为类名不会变成随机字符串。