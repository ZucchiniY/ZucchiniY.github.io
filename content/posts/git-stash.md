+++
title = "Git Stash 常用功能"
author = ["Dylan Yang"]
date = 2018-04-11T16:57:00+08:00
tags = ["stash"]
categories = ["Git"]
draft = false
+++

本文记录了如何使用 Git Stash 功能时报错的解决方案。

-   Git stash apply 的时候，报错 :

    ```text
    error Your local changes to the follow files would be overwritten by merge: xxxx
    Please commit your changes or stash them before you merge .
    ```

可以先add 修改的文件，然后再apply

```shell
git add test.txt
git stash apply
```

-   比较 stash 与当前分支的区别

    ```shell
    git stash show -p
    ```

比较指定的 stash

```shell
git stash show -p stash@{0}
```
