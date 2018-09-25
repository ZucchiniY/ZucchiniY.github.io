---
title: "忘记MySql root用户密码"
date: 2018-09-25T15:23:39+08:00
draft: false
tags: ["MySql"]
categories: ["技术"]
author: "Dylan Yang"
---

因为长时间未使用Mac上的MySql导致忘记了root密码，现在将修改root用户密码的方法记录下来。

# 正经方案

1. 关闭 mysql 服务

``` sh
sudo /usr/local/mysql/support-files/mysql.server stop
```

2. 获取管理员权限

``` sh
cd /usr/local/mysql/bin
sudo su
```

3. 重启服务

``` sh
./mysqld_safe --skip-grant-tables &
```

4. 重新找开一个终端

``` sql
use mysql;
flush privileges;
set password for 'root'@'localhost'=password('111111')
```

# 无脑方案

``` sh
cd /usr/local/mysql/bin/
sudo su
./mysqld_safe --skip-grant-tables & //这一步的作用是跨过权限验证
./mysql -uroot
```

``` sql
use mysql;
update user set authentication_string='123456' where User='root';
```