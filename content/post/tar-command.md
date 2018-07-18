---
title: "tar 命令整理"
date: 2017-03-19T22:10:21+08:00
draft: false
tags: ["tar"]
categories: ["Linux"]
author: "Dylan Yang"
---

# 命令格式

``` shell
tar [必要参数] [选择参数] [文件]
```

# 命令功能

> 用来压缩和解压文件。tar 本身不具有压缩功能。他是调用压缩功能实现的。

<!--more-->

# 命令参数

必要参数如下：

```
-A 新增压缩文件到已经存在的压缩
-B 设置区块大小
-c 建立新的压缩文件
-d 记录文件的差别
-r 添加文件到已经压缩的文件
-u 添加改变了和现有的文件到已经存在的压缩文件
-x 从压缩的文件中提取文件
-t 显示压缩文件的内容
-z 支持 gzip 解压文件
-j 支持 bzip2 解压文件
-Z 支持 compress 解压文件
-v 显示操作过程
-l 文件系统边界设置
-k 保留原有文件不覆盖
-m 保留文件不被覆盖
-W 确认压缩文件的正确性
```

可选参数如下：

```
-b 设置区块数目
-C 切换到指定目录
-f 指定压缩文件
--help 显示帮助信息
--version 显示版本信息
```

# 常见解压/压缩命令

- tar

解包：`tar xvf FileName.tar`

打包：`tar cvf FileName.tar DirName`

- .gz

解压 1：`gunzip FileName.gz`

解压 2：`gzip -d FileName.gz`

压缩 : `gzip FileName`

- .tar.gz 和 .tgz

解压：`tar zxvf FileName.tar.gzip`

压缩：`tar zcvf FileName.tar.gz DirName`

- .bz2

解压: `bzip2 -d FileName.bz2`

解压: `bunzip2 FileName.bz2`

压缩: `bzip2 -z FileName`

- tar.bz2

解压: `tar jxvf FileName.tar.bz2`

压缩: `tar jcvf FileName.tar.bz2 DirName`

- .bz

解压: `bzip2 -d FileName.bz`

解压: `bunzip2 FileName.bz`

压缩: `未知`

- .tar.bz

解压: `tar jxvf FileName.tar.bz`

压缩: `tar jcvf FileName.tar.bz DirName`

- .Z

解压: `uncompress FileName.Z`

压缩: `compress FileName`

- .tar.Z

解压: `tar Zxvf filename.tar.Z`

压缩: `tar Zcvf FileName.tar.Z DirName`


- .zip

解压: `unzip FileName.zip`

压缩: `zip FileName.zip DirName`


- .rar


解压: `rar x filename.rar`

压缩: `rar a filename.rar dirName`
