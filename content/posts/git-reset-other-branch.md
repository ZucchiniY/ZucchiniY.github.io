+++
title = "Git 强制覆盖分支"
author = ["Dylan Yang"]
date = 2019-02-27T10:22:00+08:00
tags = ["分支覆盖"]
categories = ["Git"]
draft = false
+++

今天遇到一个问题，在新分支做了一段时间开发之后，希望将此分支完全覆盖到另一分支，经过搜索，发现可以使用 `git reset --hard origin/develop` 这样就可以将 **master** 分支完全覆盖掉了。

Archived entries from file /Users/zucchini/workspace/org/blog/hugo-posts.org
