+++
title = "tree 命令"
author = ["Dylan Yang"]
date = 2018-07-05T15:31:00+08:00
tags = ["tree"]
categories = ["Linux"]
draft = false
+++

`tree` 命令在 **Linux** 里是一个非常方便的命令，可以让你方便的查看一个路径下的文件夹结构。

tree -C
: 颜色显示

tree -f
: 显示文件全路径

tree -L 2
: 只显示2层

tree -P /\*.pl
: 只显示文件目录和 **\*.pl** 为后缀的文件

tree -F
: 显示目录后面的 **\\** ，显示可执行文件 **\*** 功能类似 `ls -F`

tree --help
: 帮助手册
