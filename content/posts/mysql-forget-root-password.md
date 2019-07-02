+++
title = "忘记 MySQL Root 用户密码"
author = ["Dylan Yang"]
date = 2018-09-27T16:01:00+08:00
tags = ["Root"]
categories = ["MySQL"]
draft = false
+++

因为长时间未使用MySql导致忘记了root密码，现在将修改root用户密码的方法记录下来。


## 修改配置 {#修改配置}

```shell
vi /etc/my.cnf
```

在 **[mysqld]** 中添加 `skip-grant-tables`

例如：

```yml
[mysqld]
skip-grant-tables
datadir=/var/lib/MySQL
socket=/var/lib/mysql/mysql.sock
```


## 重启mysql {#重启mysql}

```shell
service mysql restart
```


## 用户无密码登录 {#用户无密码登录}

```shell
mysql -uroot -p (直接点击回车，密码为空)
```


## 选择数据库并修改密码 {#选择数据库并修改密码}

```sql
use mysql;
update user set authentication_string=password('123456') where user='root';
flush privileges;
```


## 删除并重启 mysql 服务 {#删除并重启-mysql-服务}

这个时候发现，确实可以用新的密码登录了， 但是操作的时候会提示：
`ERROR 1820 (HY000): You must reset your password using ALTER USER statement
before executing this statement.` 。

这是因为少了一步修改导致，执行下面的命令进行修改：

```sql
alter user 'root'@'localhost' identified by 'youpassword';
```

执行的时候发现会提示一个新的报错： `ERROR 1819 (HY000): Your password
does not satisfy the current policy requirements` ，经过搜索，发现是因为密码有要求导致，可以选择使用一个包含大小写字母、数字和符号的密码，也可以选择更新一个简单的密码：

```sql
set global validate_password_policy=0;
```

这次密码的问题就彻底解决了。
