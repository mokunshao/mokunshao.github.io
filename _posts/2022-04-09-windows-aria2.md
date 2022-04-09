---
title: Windows 安装 aria2 然后配置常驻后台
layout: post
---

## 使用 Scoop 来安装 aria2

`scoop install aria2`

## aria2 在 Windows 常驻后台运行的方法

查看 aria2 在哪个目录下：

`where aria2c`

然后在该目录下新增三个文件：`aria2.conf`，`aria.vbs`，`aria2.session`

其中 `aria2.session` 内容为空

`aria2.conf` 的内容如下：

```text
enable-rpc=true
```

`aria.vbs` 的内容如下：

```text
CreateObject("WScript.Shell").Run "aria2c.exe --conf-path=aria2.conf",0
```

然后运行 `aria.vbs` 即可，如果不运行，aria2 就不会在后台运行
