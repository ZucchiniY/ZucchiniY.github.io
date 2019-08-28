+++
title = "Mac 下执行 Git 命令报错"
author = ["Dylan Yang"]
date = 2017-12-07T15:31:00+08:00
tags = ["xcrun"]
categories = ["笔记", "Mac"]
draft = false
+++

mac 执行 git 命令时候出现 \`invalid active developer path\` ：

具体如下：

```shell
xcrun: error: invalid active developer path
(/Library/Developer/CommandLineTools), missing xcrun at:
/Library/Developer/CommandLineTools/usr/bin/xcrun
```

解决方法：

打开终端输入

```shell
xcode-select --install
```

回车后，系统弹出下载 xcode，点击确认，下载完成后即可。（实际上不是下载 xcode，可能下载 xcode 有关插件，下载时长约 1 分钟）

原因
: **出现这个错误原因猜想可能是因为之前安装过 xcode 卸载后出现的。**
