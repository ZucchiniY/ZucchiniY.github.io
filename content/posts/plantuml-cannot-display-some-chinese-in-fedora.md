+++
title = "PlantUML 在 Fedora 的中文显示乱码"
author = ["Dylan Yang"]
date = 2017-08-04T17:27:00+08:00
tags = ["plantuml", "乱码"]
categories = ["Linux"]
draft = false
+++

**默认安装 jdk 解决方案**

经过测试之后发现，无论是官方 **JDK** 还是 **OpenJDK** 都有这个问题，经过测试发现是 **JDK** 使用的中文字库不全导致的。

百度查找更换 **JDK** 字库的方案，但是都无法解决，不知道是否需要重启，后来查到，可以通过安装默认字体来解决这个问题：

```shell
sudo dnf install cjkuni-uming-fonts
```

安装之后，重新执行 **PlantUML** 代码块，中文可以正常显示。
