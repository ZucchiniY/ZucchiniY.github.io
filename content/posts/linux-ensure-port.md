---
title: "Linux下端口占用情况"
date: 2018-09-04T10:00:33+08:00
draft: false
tags: ["shell","port"]
categories: ["技术"]
author: "Dylan Yang"
---

Linux 查看启动的后台进程，可以使用下面两个命令。

### lsof

`lsof -i:<port>` 用来查看某一端口占用情况，可以查询到对应的 COMMAND PID USER TYPE。

<!--more-->

### netstat

`netstat -tunlp | grep <port>` 用于查看指定的端口号的进程情况，可以查看端口的监听情况，最后一项则是对应的 COMMAND 和 PID。