---
title: HTTP 状态码
---

### 1xx 消息

这类状态码代表请求已被接受，需要继续处理。

100 Continue：客户端应继续其请求。

101 Switching Protocols：服务器根据客户端的请求切换协议。

102 Processing：正在处理请求，但没有响应可用。

### 2xx 成功

这类状态码代表请求已成功被服务器接收、理解、并接受。

200 OK：请求已成功。

201 Created：已创建。成功请求并创建了新的资源。

202 Accepted：服务器已接受请求，但尚未处理。

204 No Content：服务器成功处理了请求，但没有返回任何内容。

### 3xx 重定向

这类状态码代表需要客户端采取进一步的操作才能完成请求。

301 Moved Permanently：被请求的资源已永久移动到新位置。

302 Found：资源被临时被移动。

304 Not Modified：资源未被修改。

### 4xx 客户端错误

这类状态码代表客户端看起来可能发生了错误，妨碍了服务器的处理。

400 Bad Request：由于明显的客户端错误，服务器不能或不会处理该请求。

401 Unauthorized：用户没有必要的凭据。

403 Forbidden：服务器已经理解请求，但是拒绝执行它。

404 Not Found：请求失败，请求所希望得到的资源未被在服务器上发现，但允许用户的后续请求。

408 Request Timeout：请求超时。

451 Unavailable For Legal Reasons：该访问由于法律原因而被拒绝。

### 5xx 服务器错误

这类状态码代表服务器无法完成明显有效的请求。

500 Internal Server Error：服务器内部错误，无法完成请求。

502 Bad Gateway：充当网关或代理的服务器，从远端服务器接收到了一个无效的请求。

503 Service Unavailable：由于临时的服务器维护或者过载，服务器当前无法处理请求。

504 Gateway Timeout：当服务器作为网关，不能及时得到响应时返回此错误代码。