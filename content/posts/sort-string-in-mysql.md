+++
title = "MySQL 将字符串按数据进行排序"
author = ["Dylan Yang"]
date = 2018-05-22T19:06:00+08:00
tags = ["CAST", "CONVERT"]
categories = ["SQL"]
draft = false
+++

自建了一个表，其中的字段为 **char** 或者 **varchar** 的类型。

我们如果直接进行的排序的话，得到的序列是字符顺序的，即 **1,10,2,20,...**
，但是我们希望得到的是 **1,2,3,4,...** 这种序列，有两种方法可以实现排序。

-   手动转换

```sql
select id from db.sql order by id + 0 desc
```

但是这种方式显得有点丑，其实 Mysql 提供了一个非常好用的函数进行操作。

-   使用函数

**CAST()** 函数和 **CONVERT()** 可以使用。

```sql
select id from db.sql order by CAST(id as SIGNED) desc
```

```sql
select id from db.sql order by CONVERT(id, SIGNED) desc
```
