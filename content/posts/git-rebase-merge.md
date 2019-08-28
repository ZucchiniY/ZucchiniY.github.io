+++
title = "Git 提交方案"
author = ["Dylan Yang"]
date = 2017-05-07T17:25:00+08:00
tags = ["merge"]
categories = ["Git"]
draft = false
+++

本文主要讨论 Git feature 与 **master(develop)** 分支冲突解决方案。

-   同步远程分支

<!--listend-->

```shell
git pull
```

发现当前的开发流有了新的提交，且与自己开发的功能有冲突。

-   Checkout 到 feature 分支

    ```shell
    git checkout feature
    ```

-   Git rebase master

<!--listend-->

```shell
git rebase master
```

-   解决冲突，将 **`=`** **>>>>** **<<<<** 中冲突的内容进行个性

-   提交解决冲突后的内容

<!--listend-->

```shell
git add .
# or
git add -A
```

-   继续 rebase 操作

<!--listend-->

```shell
git rebase --continue
```

之后可以看到 **allying: xxxx** 提示后，表示已经进行了内容的 rebase

-   切换到要提交的分支

<!--listend-->

```shell
git checkout master
```

-   将原分支 merge 到想提交的分支

<!--listend-->

```shell
git merge feature
```

-   提交到远程分支

<!--listend-->

```shell
git push -u origin master
```
