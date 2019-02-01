---
title: "刷新 Manjaro 源"
date: 2017-06-08T22:35:21+08:00
draft: false
tags: ["Manjaro 刷新源"]
categories: ["技术"]
author: "Dylan Yang"
---

刷新 *Manjaro* 源，由快到慢并指定为中国源

``` sh
sudo pacman-mirrors -gb testing -c China
```

然后更新系统：

``` sh
sudo pacman -Syyu
```
<!--more-->