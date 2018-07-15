---
title: "Git 提交方案"
date: 2017-05-07T21:51:02+08:00
draft: false
tags: ["git merge","git rebase"]
categories: ["git"]
author: "Dylan Yang"
---

# Git feature 与 master(develop)分支冲突解决方案

- 同步远程分支

``` sh
git pull
```

发现当前的开发流有了新的提交，且与自己开发的功能有冲突。

- Checkout 到 feature 分支

 ``` sh
 git checkout feature
 ```

- Git rebase master

``` sh
git rebase master
```

- 解决冲突，将 `===` `>>>>` `<<<<` 中冲突的内容进行个性

- 提交解决冲突后的内容

``` sh
git add .
# or
git add -A
```

- 继续 `rebase` 操作

``` sh
git rebase --continue
```

之后可以看到 `allying: xxxx` 提示后，表示已经进行了内容的 `rebase`

- 切换到要提交的分支

``` sh
git checkout master
```

- 将原分支 `merge` 到想提交的分支

``` sh
git merge feature
```

- 提交到远程分支

``` sh
git push -u origin master
```