---
title: Java 异常与网络
---

## Java 异常与网络

### throw 和 throws 的区别？

throw：是真实抛出一个异常。

throws：是声明可能会抛出一个异常。

### final、finally、finalize 有什么区别？

final：是修饰符，如果修饰类，此类不能被继承；如果修饰方法和变量，则表示此方法和此变量不能在被改变，只能使用。

finally：是 `try{} catch{} finally{}` 最后一部分，表示不论发生任何情况都会执行， finally 部分可以省略，但如果 finally 部分存在，则一定会执行 finally 里面的代码。

finalize： 是 Object 类的一个方法，在垃圾收集器执行的时候会调用被回收对象的此方法。

### try-catch-finally 中哪个部分可以省略？

`try-catch-finally` 其中 catch 和 finally 都可以被省略，但是不能同时省略，也就是说有 try 的时候，必须后面跟一个 catch 或者 finally。

### try-catch-finally 中，如果 catch 中 return 了，finally 还会执行吗？

finally 一定会执行，即使是 catch 中 return 了，catch 中的 return 会等 finally 中的代码执行完之后，才会执行。

### 常见的异常类有哪些？

NullPointerException: 空指针异常

ClassNotFoundException: 指定类不存在

NumberFormatException: 字符串转换为数字异常

IndexOutOfBoundsException: 数组下标越界异常

ClassCastException: 数据类型转换异常

FileNotFoundException: 文件未找到异常

NoSuchMethodException: 方法不存在异常

IOException: IO 异常

SocketException: Socket 异常

### 简述 tcp 和 udp的区别？

tcp 和 udp 是 OSI 模型中的运输层中的协议。tcp 提供可靠的通信传输，而 udp 则常被用于让广播和细节控制交给应用的通信传输。

两者的区别大致如下：

tcp 面向连接，udp 面向非连接即发送数据前不需要建立链接；

tcp 提供可靠的服务（数据传输），udp 无法保证；

tcp 面向字节流，udp 面向报文；

tcp 数据传输慢，udp 数据传输快；

### tcp 为什么要三次握手

如果采用两次握手，
那么只要服务器发出确认数据包
就会建立连接，
但由于客户端此时
并未响应服务器端的请求，
那此时服务器端就会
一直在等待客户端，
这样服务器端
就白白浪费了一定的资源。
若采用三次握手，
服务器端没有收到
来自客户端的再此确认，
则就会知道客户端
并没有要求建立请求，
就不会浪费服务器的资源。

### 说一下 tcp 粘包是怎么产生的？
tcp 粘包可能发生在
发送端或者接收端，
分别来看两端各种
产生粘包的原因：

发送端粘包：
发送端需要等缓冲区满
才发送出去，造成粘包；

接收方粘包：
接收方不及时接收缓冲区的包，
造成多个包接收。

### OSI 的七层模型都有哪些？
物理层：
利用传输介质为数据链路层提供物理连接，
实现比特流的透明传输。

数据链路层：
负责建立和管理节点间的链路。

网络层：
通过路由选择算法，
为报文或分组通过通信子网
选择最适当的路径。

传输层：
向用户提供可靠的端到端的
差错和流量控制，
保证报文的正确传输。

会话层：
向两个实体的表示层
提供建立和使用连接的方法。

表示层：
处理用户信息的表示问题，
如编码、数据格式转换和加密解密等。

应用层：
直接向用户提供服务，
完成用户希望在网络上完成的
各种工作。
