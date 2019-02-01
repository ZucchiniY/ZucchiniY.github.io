---
title: "Linux 空间占用分析"
date: 2018-05-06T21:51:02+08:00
draft: false
tags: ["du", "find"]
categories: ["技术"]
author: "Dylan Yang"
---

# find 查找大文件

``` sh
find . -type f -size +800M
```

- type 类型：`b` 块设备，`d` 目录，`c` 字符设备文档，`p` 管道文档，`l` 符号链接文档，`f` 普通文档
- name 文件名：支持通配符
- size 文件大小：`+` 表示大于， `-` 表示小于，支持 k/M/G 的单位

``` sh
find . -type f -size +800M | xargs ls -lh
```

这里的 `xargs` 是把管理参数切分成多个部分，可以将命令进行组合
<!--more-->

# du 查找大目录

``` sh
du -h --max-depth=1
du -hm --max-depth=2 | sort -n
du -hm --max-depth=2 | sort -nr | head -12
```
