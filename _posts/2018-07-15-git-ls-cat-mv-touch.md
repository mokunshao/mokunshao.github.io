---
title: 四种命令的使用
---

本文主要讲述`ls`、`cat`、`mv`和`touch`这四种命令的简单用法。

<!--more-->

## ls

`ls` 是一个常用的命令，是 list 的缩写。在不带参数的情况下执行后会显示所在目录里非隐藏文件和子目录的名称，而其他详细的信息则不显示。

`ls`的参数比较多，在此列举常用的两种：

1. `ls -a`或`ls -all`: 显示所有文件及子目录，包括隐藏文件。

2. `ls -l`: 显示文件及子目录的同时显示其详细信息。

更多`ls`的用法可以参考[这里](https://www.tecmint.com/15-basic-ls-command-examples-in-linux/)

## cat

`cat`是 Concatenate 的缩写。

`cat`可以用于查看文件内容，只需执行`cat 文件名`即可。

`cat`还可以用于创建新文件，只需执行`cat > 文件名`即可。

执行`cat 文件1 > 文件2`，文件2的内容将会变成文件1的内容。

执行`cat 文件1 >> 文件2`，文件1的内容将会添加到文件2的内容的后面。

更多`cat`的用法可以参考[这里](https://www.tecmint.com/13-basic-cat-command-examples-in-linux/)

## mv

`mv`是 Move 的缩写。

`mv`可以用来移动文件，只需执行`mv 文件名 目标目录`即可。

`mv`可以用来重命名，只需执行`mv 文件名1 文件名2`即可。

更多`mv`的用法可以参考[这里](https://www.computerhope.com/unix/umv.htm)

## touch

`touch`可以用于改变文件的时间戳，还可以用于创建空文件。

执行`touch 不存在的文件名`即可建立一个新的空文件。

执行`touch 存在的文件名`将改变文件的时间戳为当前时间。

除此之外，`touch`命令还可以自定义文件的时间戳，详见[这里](https://linux.cn/article-2740-1.html)

## 使用 explainshell.com 了解每条命令的意思

使用[explainshell.com](https://explainshell.com/)我们可以查询命令及其参数的意思什么，方便我们记忆这条命令及参数。

例如在此网站查询`pwd -p`，它会告诉我们`pwd`的意思是 print name of current/working directory，以及`-p`的意思是 physical (avoid all symlinks)。