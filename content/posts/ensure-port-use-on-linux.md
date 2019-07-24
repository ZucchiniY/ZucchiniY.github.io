+++
title = "Linux 查看端口占用情况"
author = ["Dylan Yang"]
date = 2018-09-04T10:53:00+08:00
tags = ["lsof", "netstat"]
categories = ["Linux"]
draft = false
+++

Linux 查看启动的后台进程，可以使用下面两个命令。


## lsof {#lsof}

`lsof -i:<port>` 用来查看某一端口占用情况，可以查询到对应的 COMMAND PID USER TYPE。


## netstat {#netstat}

`netstat -tunlp | grep <port>` 用于查看指定的端口号的进程情况，可以查看端口的监听情况，最后一项则是对应的 COMMAND 和 PID。
