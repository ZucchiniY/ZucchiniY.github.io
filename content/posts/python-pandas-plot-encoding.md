---
title: "Python Pandas 生成图片乱码"
date: 2018-09-17T20:30:33+08:00
draft: false
tags: ["pandas","plot"]
categories: ["技术"]
author: "Dylan Yang"
---

使用 Anaconda 进行数据处理后生成图片的时候，如果不指定对应字体会导致中文乱码，可以通过下面的方案进行解决。

``` python
form pylab import mpl
mpl.rcParams['font.sans-serif'] = ['Microsoft YaHei'] # 指定默认字体：解决plot不能显示中文问题
mpl.raParams['axes.unicode_minus'] = False # 解决保存图像是负号'-'显示为方块的问题
```
<!--more-->