+++
title = "刷新 Manjaro 源"
author = ["Dylan Yang"]
date = 2017-06-08T16:49:00+08:00
tags = ["pacman"]
categories = ["Linux"]
draft = false
+++

刷新 **Manjaro** 源，由快到慢并指定为中国源

```shell
sudo pacman-mirrors -gb testing -c China
```

然后更新系统：

```shell
sudo pacman -Syyu
```
