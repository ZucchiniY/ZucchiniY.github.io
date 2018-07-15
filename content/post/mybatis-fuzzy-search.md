---
title: "mybatis 模糊查询"
date: 2018-04-28T22:35:21+08:00
draft: false
tags: ["模糊查询","Mysql","Oracle"]
categories: ["Mybatis"]
author: "Dylan Yang"
---

# mysql

``` sql
SELECT * FROM DB.SQL WHERE MYNAME LIKE CONCAT('%' , #{myName} , '%')
```

或者使用 `${}` 来进行查询

``` sql
SELECT * FROM DB.SQL WHERE MYNAME LIKE CONCAT('%' , '${myName}' , '%')
```

# Oracle

``` sql
SELECT * FROM DB.SQL WHERE MYNAME LIKE '%'||#{myName}||'%'
```