---
title: "Git tags 常用功能"
date: 2018-06-04T22:10:21+08:00
draft: false
tags: ["git tags"]
categories: ["技术"]
author: "Dylan Yang"
---

Git tags 的基础命令的使用。
<!--more-->

- 查看

``` shell
git tag
```

- 创建

``` shell
git tag tag_name
```

- 推送

``` shell
git push origin tag_name
git push --tags # 推送所有 tags
```

- 删除

``` shell
# 删除本地
git tag -d tag_name
# 删除远程
git push origin :refs/tags/tag_name
# 需要先删除本地 tag，再删除线上
```

- 拉取

``` shell
git fatch origin tag tag_name
```