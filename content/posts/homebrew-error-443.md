+++
title = "homebrew 报错"
author = ["Dylan Yang"]
date = 2019-10-23T10:31:00+08:00
tags = ["homebrew"]
categories = ["Mac"]
draft = false
+++

今天在更新的时候，发现 homebrew 安装的时候，会报错 **curl: (7) Failed
to connect to raw.githubusercontent.com port 443: Operation timed out**
，一开始没有明白是为什么，后来单独安装的时候，发现是因为 `curl` 这个命令有问题了，使用 homebrew 重新安装一下就可以。

`brew reinstall curl`
