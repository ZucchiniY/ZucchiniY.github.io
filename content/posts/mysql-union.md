---
title: "Mysql Union操作符"
date: 2018-06-14T13:48:54+08:00
draft: false
tags: ["UNION"]
categories: ["技术"]
author: "Dylan Yang"
---

MySQL UNION 操作符用于连接两个以上的 SELECT 语句的结果到一个结果集合中。多个 SELECT 语句会删除重复的数据。

语法格式：

``` sql
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions]
UNION [ALL | DISTINCT]
SELECT expression1, expression2, ... expression_n
FROM tables
[WHERE conditions];
```
<!--more-->

参数：

- expression1,expression2,...expression_n: 要查询的列名
- tables: 要查询的表名
- WHERE conditions: 可选，查询条件
- DISTINCT: 可选，删除结果集中重复的数据。默认情况下 UNION 会删除重复数据，所以对结果无影响
- ALL: 可选，返回所有结果集，包含重复数据