---
title: "DAO层 Service 层"
date: 2017-04-25T21:51:02+08:00
draft: false
tags: ["DAO", "Service"]
categories: ["Springboot"]
author: "Dylan Yang"
---

# DAO 层

> 进行数据检查

数据访问对象，即 _Data Access Object_ ，提供单一表的 _CRUD_ 操作，也就是创建(create)、读取(select)、更新(update)、删除(delete)。另外还包括了查询方法、排序和分页方法等内容。

# Service 层

> 进行逻辑判断

可以跨多个对象，只在单一的业务线中，处理逻辑，并处理什么时候访问哪个数据对象。

# 分类

- DAO 数据库交互工作
- Modle 存放实体类
- Service 相应的业务逻辑处理

# Mybatis + Spring

- DAO 对应的是 Mapper.java，在对应的 Mapper.xml 中就可以对数据库进行操作了。
- Modle 对应的是 实体层，数据库的表的实例化对应，可以在其中增加对应的 Set/Get 方法，也可以增加需要的私有对象
- Service 写基础的方法，对应可能是几个方法的复杂组合。也可以是业务逻辑的体现
- Cotroller 写页面的访问策略，也需要处理前后端的数据传递