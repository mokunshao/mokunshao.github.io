---
title: HTML 常用元素
---

## 写在前面

强烈推荐[https://htmlreference.io](https://htmlreference.io)！

它通过大量示例和注释帮助你快速上手某个元素，对新手非常友好。

不想一上来就看文档，可以先看看这个。每个元素的页面都有相关的 MDN 链接。

想学 CSS 的话还有这个：[https://cssreference.io/](https://cssreference.io/), 也是非常赞！

<!-- more -->

## HTML 常用元素

一个基本的网页有什么元素？如果你还不知道的话，请看这里：[https://htmlreference.io/base/](https://htmlreference.io/base/)

今天我们要探讨的元素有`<iframe>`、`<a>`、`<form>`、`<input>`、`<button>`、`<label>`、`<select>`、`<textarea>`和`<table>`。这里会有它们的简单用法。

### 1. `<iframe>` 元素

`<iframe>` 元素快速入门：[https://htmlreference.io/element/iframe/](https://htmlreference.io/element/iframe/)

`<iframe>` 元素使用手册：[https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/iframe)

`<iframe>` 元素是可替代元素。

`<iframe>` 元素的 name 属性可以配合着 `<a>` 元素的 target 属性使用。此时 `<a>` 元素的 target 属性的值是 `<iframe>` 元素的 name 属性的值。点击 `<a>` 元素后将在`<iframe>` 元素展示。

示例： 

```html
<iframe name=xxx src="#"></iframe>
<a target=xxx href="http://www.qq.com">QQ</a>
<a target=xxx href="http://www.baidu.com">Baidu</a>
```

### 2. `<a>` 元素

`<a>` 元素快速入门：[https://htmlreference.io/element/a/](https://htmlreference.io/element/a/)

`<a>` 元素使用手册：[https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/a)

#### 2.1 target 属性的四个值：

1. `_self` 当前页面加载
     
2. `_blank` 新窗口打开
     
3. `_parent` 加载响应到当前浏览上下文的父浏览上下文。如果没有 parent 框架或者浏览上下文，此选项的行为方式与 `_self` 相同。
     
4. `_top` 加载响应进入顶层浏览上下文。如果没有 parent 框架或者浏览上下文，此选项的行为方式与 `_self` 相同。

#### 2.2 download 属性:

添加该属性后点击链接会保存为本地文件。

#### 2.3 href 属性:

绝对URL（或：绝对路径）

```html
href="http://www.example.com/index.htm"

href="http://www.example.com/index.htm#bottom"
<!-- 上面这个不发送请求 -->

href="http://www.example.com/index.htm?wd=qq"

href="//www.example.com/index.htm"
<!-- 上面这个是自动继承协议的绝对路径 -->
```

相对URL（或：相对路径）

```html
href="index.htm"
```

锚 URL

```html
href="#top"
<!-- 上面这个不发送请求 -->
```

伪协议

```html
href=JavaScript:alert("你好");
<!-- 伪协议是历史遗留问题 -->
```

> 参考资料：
>
> [https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Element/a)
> [http://www.w3school.com.cn/tags/att_a_href.asp](http://www.w3school.com.cn/tags/att_a_href.asp)

### 3. `<form>` 元素、`<input>` 元素、`<button>` 元素、`<label>` 元素、 `<select>` 元素以及 `<textarea>` 元素

把他们放在一起是因为这几个元素通常是和 `<form>` 元素一起出现的。

`<form>` 元素快速入门：[https://htmlreference.io/element/form/](https://htmlreference.io/element/form/)

`<input>` 元素快速入门：[https://htmlreference.io/element/input/](https://htmlreference.io/element/input/)

`<button>` 元素快速入门：[https://htmlreference.io/element/button/](https://htmlreference.io/element/button/)

`<label>` 元素快速入门：[https://htmlreference.io/element/label/](https://htmlreference.io/element/label/)

`<select>` 元素快速入门：[https://htmlreference.io/element/select/](https://htmlreference.io/element/select/)

`<textarea>` 元素快速入门：[https://htmlreference.io/element/textarea/](https://htmlreference.io/element/textarea/)

`<form>` 元素要有提交按钮，可通过 `<input>` 或 `<button>` 实现。

`<form>` 元素通常嵌套多个 `<input>` 元素。

如果`<form>` 元素的 method 属性为 GET 则默认把参数放到查询参数里面。

如果`<form>` 元素的 method 属性为 POST 则默认把查询参数放到 Form Data 里面。

`<form>` 元素也有 target 属性，和 `<a>` 一样。

示例：

```html
<form action="user" method="post">
    <input type="text" name="username">
    <input type="password" name="password">
    <input type="submit" value="提交">
</form>
```

submit 是 `<input>` 元素唯一可以提交表单的type：

```html
<input type="submit" value="注册">
```

提交表单也可以通过 `<button>` 元素实现：

```html
<button>注册</button>
```

下面这个点击后无反应，不要这样写：

```html
<input type="button" value="注册">
```

如果想要点击选项的文字也能选中，给文字加个 `<label>` 元素：

```html
<input type="checkbox" id="xxx"><label for="xxx">同意</label>

<label for="xxx">用户名</label><input type="text" id="xxx" name="username">
```

`<label>` 元素的用途是为了和 `<input>` 元素关联，`<label>` 元素的 for 属性和 `<input>` 元素的 id 属性是一对的。

另一种写法是在`<label>` 元素内嵌套 `<input>` 元素：

```html
<label><input type="checkbox">同意</label>

<label>用户名<input type="text" name="username"></label>
```

`<input>` 元素的 type 属性的值为 checkbox 时是多选。

多选示例：

```html
喜欢的水果
<label><input type="checkbox" name="fruit" value="orange">橘子</label>
<label><input type="checkbox" name="fruit" value="banana">香蕉</label>
```

 `<input>` 元素的 type 属性的值为 radio，且 name 属性相同时，是多选。

单选示例：

```html
爱我
<label><input type="radio" name="loveme" value="yes">Yes</label>
<label><input type="radio" name="loveme" value="no">No</label>
```

无论单选还是多选，代表各选项的 `<input>` 元素的 name 属性都要相同。服务器收到的信息为 name = value。

`<select>` 元素示例：

```html
<select name="group multiple>
    <option value="">-</option>
    <option value="1">第一组</option>
    <option value="2">第二组</option>
    <option value="3" disabled>第三组</option>
    <option value="4" selected>第四组</option>
</select>
```

`<textarea>` 元素示例：

```html
<textarea style="resize: none; width: 100px;" name="爱好"></textarea>
```

### 4. `<table>` 元素

`<table>` 元素是用来构建表格的。

`<table>` 元素快速入门：[https://htmlreference.io/element/table/](https://htmlreference.io/element/table/)

`<table>` 元素使用手册：[https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/table)

`<table>` 元素内要嵌套很多其他元素才能工作，参考用法见示例。

示例：

```html
<table border=1 style="border-collapse:collapse;">    
    <colgroup>        
        <col width=100>        
        <col bgcolor=red width=200>        
        <col width=300>        
        <col width=70>    
    </colgroup>    
    <thead>        
        <tr>            
            <th>姓名</th><th>班别</th><th>座号</th>        
        </tr>   
    </thead>    
    <thbody>        
        <tr>            
            <td>略</td><td>略</td><td>略</td>            
        </tr>    
    </thbody>    
    <tfoot>        
        <tr>            
            <td>略</td><td>略</td><td>略</td>        
        </tr>    
    </tfoot> 
</table>
```