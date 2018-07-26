---
title: "Fedora 下中文显示不全的解决方案"
date: 2017-08-04T22:10:21+08:00
draft: false
tags: ["Linux","PlantUML", "中文"]
categories: ["技术"]
author: "Dylan Yang"
---

# 默认安装 jdk 解决方案

经过测试之后发现，无论是官方 =JDK= 还是 _OpenJDK_ 都有这个问题，经过测试发现是 JDK 使用的中文字库不全导致的。

百度查找更换 jdk 字库的方案，但是都无法解决，不知道是否需要重启，后来查到，可以通过安装默认字体来解决这个问题：

``` sh
sudo dnf install cjkuni-uming-fonts
```

安装之后，重新执行 _PlantUML_ 代码块，中文可以正常显示。
<!--more-->