---
title: "nvm 重装 package"
date: 2018-04-23T22:10:21+08:00
draft: false
tags: ["nvm","reinstall package"]
categories: ["技术"]
author: "Dylan Yang"
---

- 更新新的node版本，将旧版本模块全部同步安装到新版本下，可以使用下面的命令:

``` bash
nvm install node --reinstall-packages-from=node
```
<!--more-->