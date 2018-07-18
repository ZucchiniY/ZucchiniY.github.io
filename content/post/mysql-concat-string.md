---
title: "Mysql 查询结果中处理字符串"
date: 2018-05-15T22:35:21+08:00
draft: false
tags: ["字符串","select"]
categories: ["MySql"]
author: "Dylan Yang"
---

# CONCAT

- 将多个结果作为字符串拼接在一起

``` sql
concat(str1,str2,...)
```

实例：

``` sql
select concat(o.user_name,o.user_number) from user o where user_id = '1'
```

但是如果查询过程中有一个字符串为 `null` 则整个结果都将是 `null`，这时可以将 `null` 转换为 ''
<!--more-->

``` sql
select concat(IFNULL(o.user_name,''),o.user_number) from user o where user_id = '1'
```

如果想将结果分隔，则可以使用下面的方法

``` sql
select concat(o.user_name,',',o.user_number) from user o where user_id = '1'
```

但是这种方式显得过于难用，如果字段多了，要写很多将分隔符，这时可以用 `concat_ws` 进行拼接。

# CONCAT_WS

- 将多个结果拼接在一起，使用指定的分隔符

``` sql
concat_ws(separator,str1,str2,...)
```

实例：

``` sql
select concat_ws(';',o.user_name,o.user_number) from user o where user_id = '1'
```

这种情况下，结果中有 `null` 的话，也不会返回 `null`，但是如果将分隔符指定为 `null` 则结果会全变成 `null`

# group_concat

- 将多行的字符串分组整合成一个字符串，必须配合 `group` 使用

``` sql
group_concat([distinct] str1 [order by asc/desc] [separator])
```

`distinct` 可以排除重复值
`order by` 可以按升序 (`asc`) 或者降序 (`desc`) 进行排序
`separator` 是分隔符，默认为 ','

实例：

``` sql
select
    o.class_id,
    group_concat(o.student_name)
from
    student o
group by
    o.class_id
```

上面这个 sql 是将学生按班级进行分组，然后将学生的姓名拼装到一起

更复杂一些的例子，可以将学生的名字、学生的学科和分数进行分组查询并拼接结果

``` sql
select
    o.name,
    group_concat(concat_ws('-', o.subject,o.score) order by o.id asc)
from
    student o
group by o.name;
```