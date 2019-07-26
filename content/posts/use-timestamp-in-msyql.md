+++
title = "MySQL 中使用时间戳"
author = ["Dylan Yang"]
date = 2018-05-08T10:44:00+08:00
tags = ["timestamp"]
categories = ["SQL"]
draft = false
+++

-   创建新记录和修改现有记录都更新方式

```sql
TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

-   创建的时候设置时间，后续的修改不再更新

```sql
TIMESTAMP DEFAULT CURRENT_TIMESTAMP
```

-   创建的时候把字段设置为 0 ，以后修改才更新

```sql
TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

-   创建时设置为给定值，以后更新会刷新这个时间

```sql
TIMESTAMP DEFAULT 'yyyy-mm-dd hh:mm:ss' ON UPDATE CURRENT_TIMESTAMP
```
