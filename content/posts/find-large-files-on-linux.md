+++
title = "Linux 空间占用分析"
author = ["Dylan Yang"]
date = 2018-05-06T10:51:00+08:00
tags = ["find", "du"]
categories = ["Linux"]
draft = false
+++

## find 查找大文件 {#find-查找大文件}

```shell
find . -type f -size +800M
```

type 类型
: **b** 块设备， **d** 目录， **c** 字符设备文档， **p** 管道文档，
    **l** 符号链接文档， **f** 普通文档

name 文件名
: 支持通配符

size 文件大小
: **+** 表示大于， **-** 表示小于，支持 k/M/G 的单位

<!--listend-->

```shell
find . -type f -size +800M | xargs ls -lh
```

这里的 `xargs` 是把管理参数切分成多个部分，可以将命令进行组合


## du 查找大目录 {#du-查找大目录}

```shell
du -h --max-depth=1
du -hm --max-depth=2 | sort -n
du -hm --max-depth=2 | sort -nr | head -12
```
