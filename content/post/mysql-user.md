---
title: "新增MySql用户"
date: 2018-07-12T16:47:58+08:00
draft: false
tags: ["MySql"]
categories: ["技术"]
author: "Dylan Yang"
---

- 创建本地用户

``` sql
create user 'test'@'localhost' identified by 'password';
```

- 创建局域网用户

``` sql
create user 'test'@'%' identified by 'password';
```

- 刷新

``` sql
flush privileges;
```

<!--more-->

- 修改密码

``` sql
set password for 'test'@'localhost' = password('newpassword');
```

如果是当前用户：

``` sql
SET PASSWORD = PASSWORD("newpassword");
```

- 授权

授权相关操作见 [Mysql 数据库设置远程权限](https://zucchiniy.github.io/blog/2016/mysql-数据库设置远程权限.html)

这里补充一下 MySql 移除权限的命令：

``` sql
REVOKE privilege ON databasename.tablename FROM 'username'@'localhost';
```

- 删除用户

``` sql
drop user 'username'@'localhost'
```