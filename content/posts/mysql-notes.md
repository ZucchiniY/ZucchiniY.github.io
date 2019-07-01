+++
title = "MySQL 连接数清理"
author = ["Dylan Yang"]
date = 2019-01-18T10:13:00+08:00
tags = ["调整连接数"]
categories = ["MySQL"]
draft = false
+++

在管理 MySQL 服务器的过程中，会出现连接时间过长的问题，分析之后发现主要是之前写的操作 MySQL 的程序未正常结束，导致资源占用过高。

这时可以使用以下的方案进行自理：

```sql
show status like 'Threads%';
show variables like '%max_connections%';
show global status like 'Max_used_connections';
show status;
show processlist;
show OPEN TABLES where In_use > 0;
```

这时可以找到真正占用数据库资源的进程，然后使用 `kill <process id>` 结束掉进程。

Archived entries from file /Users/zucchini/workspace/org/blog/hugo-posts.org
