---
title: 前端性能优化
---

## 影响性能的关键因子

* 延迟

* 带宽

* 静态资源大小

* TCP 握手时间

* SSL 握手时间

* DNS 解析时间

* ...

## 方法

### CDN

CDN 可以降低延迟。因为与服务器的物理距离越近，延迟越低。

CDN 通常不带 cookies，这是优点。

### Cache（缓存）

缓存是最快的，相比任何服务器或 CDN。

通过 Cache-Control HTTP 标头合理制定缓存。

真正的静态元素也许可以被设置为永远可用。

使用 hash tag。

Etag 也是有性能消耗的。

###  带宽

* 延迟加载资源

> 例如图片懒加载（Chrome 浏览器原生支持 img 的懒加载）

* 提前加载资源

> 例如 preload prefetch

* 不加载资源

> 通过 Cache

### 资源文件

对数据压缩优化

* Gzip, Broti。

* HTTP 2.0

> 头文件压缩，HPACK

* 代码压缩，降低可读性

> 例如 uglify.js 

* 移除无用的代码

> 例如 PurgeCSS，Tree Shaking

* 移除重型的库

### DNS prefetch

淘宝首页也使用 DNS prefetch。

### 限制 Domain 数量

控制第三方的 domain 数量。

不要使用 Domain sharding。

### 减少 TCP 创建开销

减少页面重定向，因为每次重定向都要重新建立 TCP 连接。SPA 的重定向少。

使用 CDN 带来的更低的延迟意味着更少的 TCP 开销。

### 终极方式

HTTP 2.0

## 性能优化的思路

1. 理解 Web 工作原理，认识网站性能影响因子。

2. 使用 PageInsight 等工具出具性能测试报告。

3. 使用 Chrome Devtools 寻找突破口。

4. 使用正确的方法解决性能问题。