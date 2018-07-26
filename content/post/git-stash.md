---
title: "Git Stash 常用功能"
date: 2018-04-11T22:10:21+08:00
draft: false
tags: ["git stash"]
categories: ["技术"]
author: "Dylan Yang"
---

本文记录了如何使用 Git Stash 功能时报错的解决方案。
<!--more-->

- Git stash apply 的时候，报错 :

```text
error Your local changes to the follow files would be overwritten by merge: xxxx
Please commit your changes or stash them before you merge .
```

可以先add 修改的文件，然后再apply

``` bash
git add test.txt
git stash apply
```

- 比较 stash 与当前分支的区别

``` bash
git stash show -p
```

比较指定的 stash

``` bash
git stash show -p stash@{0}
```