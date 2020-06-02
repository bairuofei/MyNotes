---
title: Ubuntu16.06 rosdep init Error & rosdep update <connection refused>
date: 2020-2-24 22:52:56
layout: post
comments: on
tags: [ros]
categories: 
---
本文记录了安装ROS时`sudo rosdep init`命令和`rosdep update`命令出错时的解决办法。
<!-- more -->

```bash
sudo rosdep init
ERROR: cannot download default sources list from:
https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/sources.list.d/20-default.list
Website may be down.
```

> 原因可能是该网站的域名服务器设置有问题，后面通过修改dns域名服务文件解决了这个问题

## 解决步骤一

实际翻墙后测试上面网站可以访问,网站内容是一个简单文本。

通过手动建立

```bash
sudo mkdir -p /etc/ros/rosdep/sources.list.d
cd /etc/ros/rosdep/sources.list.d
touch 20-default.list
sudo gedit 20-default.list
```

将上述网站中的文本信息copy到`20-default.list`中并保存。

> 上述操作实际上完成了命令`sudo rosdep init`的工作，因此后面直接执行`rosdep update`。否则重复执行`sudo rosdep init`终端会出现`20-default.list`已经存在的错误。

## 解决步骤二

在终端输入`rosdep update`，发现出现connection refused错误。

```bash
<urlopen error [Errno 111] Connection refused> (https://raw.githubusercontent.com/ros/rosdistro/master/rosdep/osx-homebrew.yaml)
```

解决办法：

```bash
sudo gedit /etc/resolv.conf
# 将原有的nameserver这一行注释，并添加以下两行：
nameserver 8.8.8.8 #google域名服务器
nameserver 8.8.4.4 #google域名服务器
# 保存退出，执行
sudo  apt-get update
rosdep update
```

通过执行上述命令可以成功安装，命令行提示：

```bash
updated cache in ...
```

>注意，每次重启计算机后，上述文件修改会失效，需要重新修改

## 参考博客

[ubuntu安装ROS进行到rosdep update时出现错误，如ERROR: unable to process source ...](https://blog.csdn.net/mrh1714348719/article/details/103803110)
[ROS:sudo rosdep init出错常规方法都无效后解决办法记录](https://zhuanlan.zhihu.com/p/77483614)