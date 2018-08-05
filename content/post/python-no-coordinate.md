---
title: "No Coordinate 报错"
date: 2018-08-05T18:08:42+08:00
draft: false
tags: ["No Coordinate报错"]
categories: ["技术"]
author: "Dylan Yang"
---

今天在学习*python*数据处理的时候报错`No coordinate is specified for {}".format(name))`，测试后发现是因为新版的**pyecharts**并未安装相关地图的js文件，所以需要单独安装：

``` shell
pip install echarts-countries-pypkg
pip install echarts-china-provinces-pypkg
pip install echarts-china-cities-pypkg
pip install echarts-china-counties-pypkg
pip install echarts-china-misc-pypkg
```
<!--more-->

安装之后，发现还是会报这个错，经过测试发现是数据中的区县并未在地图中有记录，所以需要再对数据做一次清洗。

> 但是有的人也不会报错，可能和 Python 的版本有关。

可以在将数据使用 `get_coordinate` 方法进行处理，如果结果为 `None` 则不处理此数据。