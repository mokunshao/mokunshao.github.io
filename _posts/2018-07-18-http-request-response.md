---
title: HTTP 的请求与响应
---

## HTTP 是什么

HTTP，全称 HyperText Transfer Protocol，中文名为超文本传输协议，这个协议采用一种明文的方式来传输我们的内容，没有任何的加密。几乎所有网页都采用 HTTP 协议或者 HTTPS 协议。目前 HTTP 协议的最新版本为 HTTP/2。

## HTTP 的请求

每当我们访问一个网页，我们都在向这个网站的服务器发送请求（Request），请求的方式有八种：`GET`、`HEAD`、`POST`、`PUT`、`DELETE`、`TRACE`、`OPTIONS` 和 `CONNECT`。

下面是一个请求报文：

```
GET / HTTP/1.1
Host: www.baidu.com
Connection: keep-alive
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/67.0.3396.99 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7
```

请求报文包括以下几个部分：

### 1. Start line

Start line 在请求报文的第一行，主要包括请求方法、请求路径和协议及其版本号。

```
GET / HTTP/1.1
```

### 2. Headers

Headers 的基本结构是` Key: value1`，Headers 可分为 General headers，Request headers 和 Entity headers。具体内容请参见[MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages)
。

```
Host: www.baidu.com
Connection: keep-alive
Cache-Control: max-age=0
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/67.0.3396.99 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Accept-Encoding: gzip, deflate, br
Accept-Language: zh-CN,zh;q=0.9,en-US;q=0.8,en;q=0.7
```

### 3. Body

除了`POST`以外，并非所有 Request 都有 Body，例如`GET`、`HEAD`、`DELETE` 和 `OPTIONS` 的 Request 通常没有 Body。

Request 的 Body 可以分为两类：Single-resource bodies 和 Multiple-resource bodies，具体内容请参见[MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages)。

### 通过 Chrome 的开发者工具查看 HTTP 请求的内容

1. 按键盘的`f12`键。

2. 选择`Network`。

3. 点击你想查看的对象。

4. 在`Request Headers`处点击`view source`。

请注意：如果网站采用 HTTP/2 的话则没有`view source`选项。

## HTTP 的响应

当一个网站的服务器接收到我们的请求，服务器会向我们作出响应（Response）。

下面是一个响应报文：

```
HTTP/1.1 200 OK
Bdpagetype: 1
Bdqid: 0x964b39ad00058174
Cache-Control: private
Connection: Keep-Alive
Content-Encoding: gzip
Content-Type: text/html
Cxy_all: baidu+4ed01c99ed7b28c243187a264ce1b08a
Date: Wed, 18 Jul 2018 06:19:17 GMT
Expires: Wed, 18 Jul 2018 06:18:52 GMT
Server: BWS/1.1
Set-Cookie: BDSVRTM=0; path=/
Set-Cookie: BD_HOME=0; path=/
Set-Cookie: H_PS_PSSID=26654_1425_21113_22073; path=/; domain=.baidu.com
Strict-Transport-Security: max-age=172800
Vary: Accept-Encoding
X-Ua-Compatible: IE=Edge,chrome=1
Transfer-Encoding: chunked
```

响应报文包括以下几个部分：

### 1. Status line

Status line 在响应报文的第一行，主要包括协议及其版本号、状态码和状态信息。

```
HTTP/1.1 200 OK
```

### 2. Headers

Headers 的基本结构是` Key: value1`，Headers 可分为 General headers，Response headers 和 Entity headers。具体内容请参见[MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages)。

```
Bdpagetype: 1
Bdqid: 0x964b39ad00058174
Cache-Control: private
Connection: Keep-Alive
Content-Encoding: gzip
Content-Type: text/html
Cxy_all: baidu+4ed01c99ed7b28c243187a264ce1b08a
Date: Wed, 18 Jul 2018 06:19:17 GMT
Expires: Wed, 18 Jul 2018 06:18:52 GMT
Server: BWS/1.1
Set-Cookie: BDSVRTM=0; path=/
Set-Cookie: BD_HOME=0; path=/
Set-Cookie: H_PS_PSSID=26654_1425_21113_22073; path=/; domain=.baidu.com
Strict-Transport-Security: max-age=172800
Vary: Accept-Encoding
X-Ua-Compatible: IE=Edge,chrome=1
Transfer-Encoding: chunked
```

### 3. Body

并非所有 Response 都有 Body，例如状态码为`201`和`204`的 Response 通常没有 Body。

Response 的 Body 可以分为三类：Single-resource bodies consisting of a single file of **known** length，Single-resource bodies consisting of a single file of **unknown** length 和 Multiple-resource bodies。具体内容请参见[MDN](https://developer.mozilla.org/en-US/docs/Web/HTTP/Messages)
。

### 通过 Chrome 的开发者工具查看 HTTP 响应的内容

1. 按键盘的`f12`键。

2. 选择`Network`。

3. 点击你想查看的对象。

4. 在`Response Headers`处点击`view source`。

请注意：如果网站采用 HTTP/2 的话则没有`view source`选项。

## 使用 curl 命令

curl 是利用 URL 语法在命令行方式下工作的开源文件传输工具。接下来将说明如何使用 curl 发送 GET 和 POST 请求。

### 使用 curl 发送 GET 请求

```
curl http://www.example.com
```

或者这条命令，两者的效果是一样的：

```
curl -G http://www.example.com
```

不过我推荐使用这个命令，执行后可以看到 header data 的同时略去 progress meter 或者 error messages：

```
curl -v -s http://www.example.com
```

你也可以往命令添加更多参数，详见[这里](http://man.linuxde.net/curl)。

### 使用 curl 发送 POST 请求

你可以使用这条命令：

```
curl -d "要提交的内容" http://www.example.com
```

或者这条命令，两者的效果是一样的：

```
curl -X POST -d "要提交的内容" http://www.example.com
```

不过我推荐使用这个命令，执行后可以看到 header data 的同时略去 progress meter 或者 error messages：

```
curl -d "要提交的内容" -v -s http://www.example.com
```

你也可以往命令添加更多参数，详见[这里](http://man.linuxde.net/curl)。