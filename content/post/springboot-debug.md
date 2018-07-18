---
title: "Springboot logging 配置"
date: 2018-04-24T22:10:21+08:00
draft: false
description: "Springboot 在 yml 配置文件中如何打印日志"
tags: ["logging","springboot"]
categories: ["Springboot"]
author: "Dylan Yang"
---

- 打印 Mybatis 中调用的 Sql

``` yml
logging:
  level:
    com.xxxx.mapper: DEBUG
```
<!--more-->

> com.xxxx.mapper 是 Mybatis 接口的影射文件包

- Logger 日志按级别打印

``` yml
logging:
    level:
        org.springframework.web: DEBUG
```

> 其中，日志级别有： **ERROR** **WARN** **INFO** **DEBUG** **TRACE**

- root 的日志级别设置

``` yml
logging:
    level:
        root: DEBUG
```