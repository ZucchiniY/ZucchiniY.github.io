---
title: "Mysql 中的时间戳使用方式"
date: 2018-05-08T22:35:21+08:00
draft: false
tags: ["时间戳","自动更新"]
categories: ["MySql"]
author: "Dylan Yang"
---

- 创建新记录和修改现有记录都更新方式

``` SQL
TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

- 创建的时候设置时间，后续的修改不再更新

``` SQL
TIMESTAMP DEFAULT CURRENT_TIMESTAMP
```
<!--more-->

- 创建的时候把字段设置为 0 ，以后修改才更新

``` SQL
TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

- 创建时设置为给定值，以后更新会刷新这个时间

``` SQL
TIMESTAMP DEFAULT 'yyyy-mm-dd hh:mm:ss' ON UPDATE CURRENT_TIMESTAMP
```