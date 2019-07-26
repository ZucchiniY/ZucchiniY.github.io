+++
title = "MyBatis 模糊查询"
author = ["Dylan Yang"]
date = 2018-04-28T15:14:00+08:00
tags = ["模糊查询"]
categories = ["SQL"]
draft = false
+++

## mysql {#mysql}

```sql
SELECT * FROM DB.SQL WHERE MYNAME LIKE CONCAT('%' , #{myName} , '%')
```

或者使用 **${}** 来进行查询

```sql
SELECT * FROM DB.SQL WHERE MYNAME LIKE CONCAT('%' , '${myName}' , '%')
```


## Oracle {#oracle}

```sql
SELECT * FROM DB.SQL WHERE MYNAME LIKE '%'||#{myName}||'%'
```
