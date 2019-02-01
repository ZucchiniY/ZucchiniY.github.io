---
title: "Mac 下执行 Git 命令报错"
date: 2017-12-07T22:10:21+08:00
draft: false
tags: ["xcrun","Mac OS", "xcrun error"]
categories: ["技术"]
author: "Dylan Yang"
---

mac 执行 git 命令时候出现 `invalid active developer path` ：
<!--more-->
具体如下：

``` sh
xcrun: error: invalid active developer path

(/Library/Developer/CommandLineTools), missing xcrun at: 

/Library/Developer/CommandLineTools/usr/bin/xcrun
```

解决方法：

打开终端输入

``` sh
xcode-select --install
```

回车后，系统弹出下载 xcode，点击确认，下载完成后即可。（实际上不是下载 xcode，可能下载 xcode 有关插件，下载时长约 1 分钟）

> 出现这个错误原因猜想可能是因为之前安装过 xcode 卸载后出现的。
