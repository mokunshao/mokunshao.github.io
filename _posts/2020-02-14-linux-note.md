---
title: Linux 笔记
---

## 登录服务器（ssh）

```shell
ssh 用户名@地址
```

## 免密登录服务器（ssh）

生成密钥，如果本地已经有了就不要生成了：

```shell
ssh-keygen -t rsa
```

将密钥添加到远程服务器：

```shell
ssh-copy-id 用户名@地址
```

现在登录就不需要密码了：

```shell
ssh 用户名@地址
```

## 常见目录（CentOs）

`/` 根目录

`/root` root 用户的家目录

`/home/username` 普通用户的家目录

`/etc` 配置文件目录

`/bin` 命令目录

`/sbin` 管理命令目录

`/usr/bin` `/usr/sbin` 系统预装的其他命令

 ## 帮助命令

`man`：manual 的意思

`help`：内部命令（即 shell 自带命令）使用 `help` ，外部命令使用  `--help`

`info`：比 `help` 更详细

## cd

`cd -` 进入上次的目录

## mkdir

`mkdir -p` 生成多级目录

## 常用通配符

`*` 匹配任何字符

`?` 匹配 1 个字符

`[xyz]` 匹配 xyz 任意一个字符

`[a-z]` 匹配一个范围的字符

`[!xyz]` 或 `[^xyz]` 不匹配

