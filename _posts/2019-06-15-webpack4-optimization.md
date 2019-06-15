---
title: Webpack4 打包优化
---

本文适用于 Webpack4。

### 如何分析页面打包问题？

1，初级分析：使用 Webpack 内置的 stats

stats 是构建的统计信息。

可以在 package.json 中使用 stats，也可以在 Node API 中使用 stats。

2，速度分析：使用 speed-measure-webpack-plugin

可以看到每个 loader 和插件的执行耗时。

3，体积分析：使用 webpack-bundle-analyzer

### 构建速度优化策略

- 使用最新版本的 Webpack

- 多进程/多实例构建

资源并行解析可选方案：thread-loader，parallel-webpack，HappyPack。

并行压缩：parallel-uglify-plugin，开启 parallel 参数的 uglifyjs-webpack-plugin。

- 分包

分包-设置 Externals：使用 html-webpack-externals-plugin。

进一步分包-预编译资源模块：使用 DLLPlugin 进行分包，DllReferencePlugin 对 manifest.json 引用。

- 缓存

使用 HardSourceWebpackPlugin 或者 cache-loader。

- 缩小构建目标

例如 babel-loader 不解析 node_modules

### 构建体积优化策略

- Scope Hoisting

使用 Webpack 内置的 ModuleConcatenationPlugin

- Tree-shaking

Webpack 默认支持，在 `.babelrc` 里设置 `modules: false` 即可。

- 公共资源分离

Webpack3 使用 CommonsChunkPlugin

Webpack4 使用 SplitChunksPlugin

- 图片压缩

使用 image-webpack-loader

- 动态 Polyfill

方案有 babel-polyfill，babel-plugin-transform-runtime，polyfill-service。