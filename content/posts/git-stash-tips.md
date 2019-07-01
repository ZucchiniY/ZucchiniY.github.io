+++
title = "Git stash 使用"
author = ["Dylan Yang"]
date = 2019-03-01T16:17:00+08:00
tags = ["stash"]
categories = ["Git"]
draft = false
+++

在使用 Git 的时候，经常会将修改暂存，然后换一种实现方案，或者是拉取新的代码，然后将暂存的内容覆盖到当前分支，之前一直使用的是 `git apply`
命令进行操作的，今天在查看分支的时候发现 `git stash apply` 之后，并没有将已经应用过的内容删除掉，这时可以使用 `git stash drop` 掉分支，但是为什么不能直接将已经应用的功能移除掉呢？

查看了一下文档，发现如果希望在应用的同时从列表中移除，可以使用 `git
stash pop` 命令，但是这样只能操作最近的一次 stash 的内容，而 `git stash
apply` 可以指定希望应用的内容。

同样的道理，如果我们希望使用好几种实现方案来看看哪一个才是最好用的，可以多次 stash 然后使用 `git stash apply stash@{0}` 等方法来实现，可是在这样的操作中，要频繁的操作，有没有什么好的方法能直接把所有的暂存内容都查看一遍呢？

如果只是想看都暂存过哪些，可以使用 `git stash list` 查看整个的暂存列表，如果记得的话，可以下决定使用哪一个了，但是如果想看到底哪一个才是好用的那个呢？具体有什么区别呢？可以使用 `git stash save` 来查看对应的所有的修改，这样就可以非常方便的找到最好的实现方案了。

Archived entries from file /Users/zucchini/workspace/org/blog/hugo-posts.org
