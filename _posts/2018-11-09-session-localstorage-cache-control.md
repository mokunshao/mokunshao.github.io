---
title: Session、LocalStorage、Cache-Control
---

## Cookie 和 Session 的区别

Cookie 是服务器通过 Set-Cookie 头给客户端一串字符串。浏览器得到 Cookie 之后，每次访问相同域名的网页时都要带上 Cookie。

Session，简而言之就是在服务器上保存用户操作的历史信息。服务器使用 Session ID 来标识 Session，Session ID 由服务器负责产生，具有随机性与唯一性。

Session 一般是基于 Cookie 实现的，服务器保存了所有的 Session，能够根据不同的 Session ID 做出不同的响应。服务器将 Session ID 通过 Cookie 发给客户端，浏览器每次访问该域名时都会在请求头通过 Cookie 把 Session ID 告知服务器。

Cookie 储存在客户端。Session 储存在服务器。

用户可以篡改 Cookie，安全性不足，Session 的 Session ID 不能被猜到，安全性较高。

服务器的 Session 多了对性能要求高，如果想减轻负担的话用 Cookie。

## Cookie 和 LocalStorage 的区别

Cookie 允许容量较小（4KB），LocalStorage 允许容量较大（5MB）。

Cookie 会被附加在每个 HTTP 请求中，产生额外流量。LocalStorage 和 HTTP 无关，不会产生流量。

Cookie 用于保存 Session ID 等跟用户信息有关的内容，Localstorage 用来保存其他不太重要的内容。

## LocalStorage 和 SessionStorage 的区别

SessionStorage 会在页面会话结束时清除。

localStorage 永久保存，除非用户自行清除。

## Cookie 如何设置过期时间？如何删除 Cookie？

在 HTTP 响应头设置 Expires，Cache-Control 均可设置过期时间。

Expires 可以设置未来过期的具体时间。

Cache-Control 可以通过设置 max-age 设置过期的剩余时间。

默认的 Cookie 过期时间为直到关闭浏览器。

Cookie 可以通过把 Expires 属性设置为已经过去的时间即可删除。

Cookie 还可以通过通过浏览器的开发者工具删除，也可以通过浏览器的清除浏览数据功能删除。

## Cache-Control: max-age=1000 缓存 与 ETag 的「缓存」有什么区别？

`Cache-Control: max-age=1000` 在指定时间内重新载入页面时不会发送请求，只有超过指定时间后载入页面才会发送请求并下载内容。

如果 ETag 值不变，重新载入页面时只发送请求而不下载内容，如果 ETag 值变了再请求才会下载内容。

`Cache-Control: max-age=1000` 不需要发送 HTTP 请求，而 ETag 需要发送 HTTP 请求。

`Cache-Control: max-age=1000` 直接使用本地的缓存，Etag 需要发送请求后再决定是否使用缓存，速度上 `Cache-Control: max-age=1000` 更快。