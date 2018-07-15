---
title: "Linux 的 grep 命令"
date: 2018-05-31T22:10:21+08:00
draft: false
tags: ["grep"]
categories: ["Linux"]
author: "Dylan Yang"
---

# 简介

`grep` 是一个强大的文本搜索工具，支持正则表达式搜索文本并把匹配的行打印出来。

## 常规用法

``` shell
grep [-acinv] [--color=auto] 'string to search' filename
```

- `-a` : 将二进制文件以 *text* 文件的方式搜索数据 
- `-c` : 计算找到的字符串的次数
- `-i` : 忽略大小写的不同
- `-n` : 输出行号
- `-v` : 反向选择，即输出没有 「字符串」的内容
- `--color=auto` : 将找到的关键词部分加上颜色

## 示例

### 搜索 root

`grep root temp.txt` 或者 `cat temp.txt | grep root`

### 搜索 root 同时显示 这些行的行号

`grep -n root temp.txt`

### 搜索没有 root 的行

`grep -v root temp.txt`

### 搜索没有 root 和 nologin 的行

`grep -v root temp.txt | grep -v nologin`

### 搜索 root 并显示出行号和前两行与后三行

`grep -n -A3 -B2 --color=auto 'root'`

### 递归查找目录

``` shell
grep 'title' # 在当前目录搜索
grep -r 'title' # 在当前目录及其子目录搜索
grep -r -l 'title' # 在当前目录及其子目录下搜索但不输入匹配的行，只显示文件
```

## grep 与正则表达式

`grep -n 't[ea]st' temp.txt'`

匹配 *test* 和 *tast* 两个单词的行。

`grep -n '[^g]oo' temp.txt`

匹配含有 *oo* 的行，便是不能是 *goo* 内容。

更多内容见[通配符和正则表达式](https://zucchiniy.github.io/blog/2018/%E9%80%9A%E9%85%8D%E7%AC%A6%E5%92%8C%E6%AD%A3%E5%88%99%E8%A1%A8%E8%BE%BE%E5%BC%8F.html)