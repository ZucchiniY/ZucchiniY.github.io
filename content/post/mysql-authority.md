---
title: "Mysql 数据库设置远程权限"
date: 2016-04-29T22:10:21+08:00
draft: false
tags: ["Remote Connection"]
categories: ["技术"]
author: "Dylan Yang"
---

# 设置访问单个数据库权限
- 设置用户名为 root，密码为空，可以访问数据库 test
``` sh
mysql>grant all privileges on test.* to 'root'@'%';
```

# 设置访问全部数据库权限
- 设置用户名为 root，密码为空，可以访问所有数据库
``` sh
mysql>grant all privileges on *.* to 'root'@'%';
```
<!--more-->

# 设置指定用户名访问权限
- 指定用户名为 liuhui，密码为空，可以访问所有数据库
``` sh
mysql>grant all privileges on *.* to 'liuhui'@'%';
```

# 设置密码访问权限
- 设置用户名为 liuhui，密码为 liuhui，可以访问所有数据库
``` sh
mysql>grant all privileges on *.* to 'liuhui'@'%' IDENTIFIED BY 'liuhui';
```

# 设置指定可访问主机权限
- 设置用户名为 liuhui，密码为 liuhui，可以访问所有数据库，只有 10.1.1.1 这台机器有权限访问
``` sh
mysql>grant all privileges on *.* to 'liuhui'@'10.1.1.1';
```

# 设置对应的密码级别
- 参数解释
 - _validate_password_dictionary_file_
	用于难密码强度的字典文件路径
 - _validate_password_length_
	密码最小长度，参数默认为 8，
 - _validate_password_mixed_case_count_
	密码至少要包含的小写字母个数和大写字母个数
 - _validate_password_number_count_
	密码至少要包含的数字个数
 - _validate_password_policy_
	密码强度难 0/LOW 1/MEDIUM 2/STRONG
 - _validate_password_special_char_count_
	密码至少要包含的特殊字符数

``` sh
mysql>show variables like 'validate_password%';
```
