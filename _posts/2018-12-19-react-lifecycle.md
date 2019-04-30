---
title: React 生命周期
---

# 推荐 setState 的地方

componentDidMount

componentWillReceiveProps（deprecated，不再建议使用）

onClick

# shouldComponentUpdate 为什么重要

手动决定是否更新，避免不必要的更新。

优化更新的效率。

# 所有的生命周期钩子

constructor

getDerivedStateFromProps

shouldComponentUpdate

render

getSnapshotBeforeUpdate

componentDidMount

componentDidUpdate

componentWillUnmount

# Ajax 应该在哪个生命周期钩子发出

componentDidMount

原因：

1. constructor 不能 setState 

2. componentWillMount 会因为 fiber 不稳定

# 用户点击按钮调用 setState 时会更新哪些钩子

shouldComponentUpdate

componentWillUpdate（deprecated，不再建议使用）

render

componentDidUpdate