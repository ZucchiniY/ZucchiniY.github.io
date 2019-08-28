+++
title = "新增 MySQL 用户"
author = ["Dylan Yang"]
date = 2018-07-12T15:17:00+08:00
tags = ["user"]
categories = ["SQL"]
draft = false
+++

-   创建本地用户

<!--listend-->

```sql
create user 'test'@'localhost' identified by 'password';
```

-   创建局域网用户

<!--listend-->

```sql
create user 'test'@'%' identified by 'password';
```

-   刷新

<!--listend-->

```sql
flush privileges;
```

-   修改密码

<!--listend-->

```sql
set password for 'test'@'localhost' = password('newpassword');
```

如果是当前用户：

```sql
SET PASSWORD = PASSWORD("newpassword");
```

-   授权

授权相关操作见 [Mysql 数据库设置远程权限](https://zucchiniy.github.io/2016/mysql-authority-config/)

这里补充一下 MySql 移除权限的命令：

```sql
REVOKE privilege ON databasename.tablename FROM 'username'@'localhost';
```

-   删除用户

<!--listend-->

```sql
drop user 'username'@'localhost'
```
