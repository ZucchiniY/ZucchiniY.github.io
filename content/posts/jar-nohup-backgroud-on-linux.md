+++
title = "Linux 后台运行 Jar 包"
author = ["Dylan Yang"]
date = 2018-08-29T17:03:00+08:00
tags = ["nohup", "jar"]
categories = ["笔记"]
draft = false
+++

在部署 Java 程序的时候，最简单的方式就打成 **jar** 并使用 `java -jar xxxx.jar` 运行，但是如果是一台 **Linux** 服务器，执行远程上去之后，如果断开链接会中断服务，经过测试，可以通过下面的命令执行：

```shell
nohup java -jar xxxx.jar &
```

但是这样会在 **nohup.out** 生成日志，如果日志过大，则可以通过 `cp /dev/null nohup.out` 进行清理。
