+++
title = "Liquibase 子标签"
author = ["Dylan Yang"]
date = 2019-04-17T15:06:00+08:00
tags = ["Liquibase"]
categories = ["Java"]
draft = false
+++

今天在准备重构一项目，本来想用一些轻量级的模块替换掉现在使用的
_MyBatis_ 和 _Springboot_ 但是最后发现自己将这些功能集成在一起也是一个非常复杂的事儿，所以决定在项目内容进行优化，也不是重新开始构造项目。

在对数据库改造的时候，发现了个问题，针对我现在的数据库，变更和修改是一个非常复杂的事，所以在之前的测试中，引入了 **Liquibas** 进行管理。

在 **Liquibase** 是默认使用 _xml_ 进行管理的，但是写的时候非常麻烦，所以决定使用 _yaml_ 进行管理。


## changeSet {#changeset}

用来表示一次变更，我在项目中，一般是指定的新建表，修改表结构等内容，在使用的时候，按表进行管理，从 1-0 开始使用，每次修改都增加一个数。

一般我们在使用的时候，主要的就是 _id_ , _author_ 这两个，然后住所特殊的操作再调整具体的方案。

```yaml
databaseChangeLog:
  - changeSet:
    id: 1-0
    author: your_name
    changes:
```


## include {#include}

我在一个主要的文件中，将所有的变更操作都单独放到一个文件夹中，然后再引用的时候，使用 _include_ 的方式引用，当然如果要将所有文件都引入进来，可以使用 _includeAll_ 来操作，但具体的使用是不一样的：

```yaml
databaseChangeLog:
- include:
file: path/file.yml
- includeAll:
path: path
```

目前就使用过这两种方案，还有一个就是使用 Sql 文件执行操作，我现在是将一写默认数据放在这里进行管理，这样就可以简单整体的操作了。


## 引用 Sql 脚本进行操作 {#引用-sql-脚本进行操作}

```yaml
- changeSet:
  id: 1
  author: your_name
  changes:
  - slqFile:
    encoding: utf8
    path: classpath: path/file.sql
```

Archived entries from file /Users/zucchini/workspace/org/blog/hugo-posts.org
