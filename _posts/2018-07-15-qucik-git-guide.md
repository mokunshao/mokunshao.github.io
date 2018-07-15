---
title: 快速上手 Git
---

## Git 是什么？

Git 是一个相当流行的分布式版本控制系统。简单地说，Git 可以帮助我们记录文件的所有变化状态，并且可以像搭乘时光机一样，随时恢复到过去某个版本的状态。借助 Git，我们可以知道文件什么时候被什么人添加、修改以及删除。
<!-- more -->
## 下载与安装

中国大陆的 Windows 用户从这个镜像下载 Git，速度会快很多，而且版本保持最新：[https://npm.taobao.org/mirrors/git-for-windows/](https://npm.taobao.org/mirrors/git-for-windows/)

## 配置

安装好后首先要在 Git Bash 里输入以下命令，以后你在本地的修改都是以这个身份进行。

```
git config --global user.name 输入你的名字
git config --global user.email 输入你的邮箱
```

>大多数 Git 服务器都会选择使用 SSH 公钥来进行授权。系统中的每个用户都必须提供一个公钥用于授权，没有的话就要生成一个。

如果我们需要向类似 Github 这样的网站授权的话，照着以下两篇文章的步骤去做即可：

1. [Generating a new SSH key](https://help.github.com/articles/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent/#generating-a-new-ssh-key)

2. [Adding a new SSH key to your GitHub account](https://help.github.com/articles/adding-a-new-ssh-key-to-your-github-account/)

## 三个常用的 Git 命令

首先我们先进入到目标文件夹，假设文件夹在桌面而且名字为`project`,通过命令行的话我们在 Git bash 可以使用`cd ~/Desktop/project`进入。

还有另外一种方法，直接打开`project`文件夹，然后鼠标右键选择`Git bash here`进入。

### git init

通过`git init`命令我们可以对这个目录（文件夹）进行初始化，创建新的 Git 仓库。此时目录内会生成`.git`子目录。

![git-init-success](https://raw.githubusercontent.com/mokunshao/images/master/git-init-success.PNG)

### git add

每当我们增加、修改或者删除文件后，需要使用`git add`命令来将修改添加到暂存区。直接执行`git add`是会报错的，所以我们通常会在`add`的后面添加上空格和文件名，亦或者使用`git add .`和`git add *`。在执行`git commit`前必须先执行`git add`。

![git-add](https://raw.githubusercontent.com/mokunshao/images/master/git-add.PNG)

### git commit -v

`git commit`命令会把暂存区的所有内容提交到当前分支。执行`git commit -v`命令后，我们可以看到所有目录里的所有变化，此时我们可以输入本次提交的说明，然后按`Esc`退出编辑模式，再输入`:wq`就可退出这个界面。如果你没有输入提交说明就退出的话会提示 commit 失败。

![git-commit-v](https://raw.githubusercontent.com/mokunshao/images/master/git-commit-v.PNG)

请注意，在 Push 之前请在 Github 上新建一个和该目录同名的仓库，并且运行 Github 提供的几句命令行，否则会出错，无法 Pull 和 Push，因为没人知道你要从哪里 Pull 以及 Push 到哪里。