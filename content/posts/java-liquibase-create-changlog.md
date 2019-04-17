+++
title = "Java Liquibase 生成 changelog.xml"
author = ["Dylan Yang"]
date = 2019-04-17T09:27:00+08:00
tags = ["Liquibase"]
categories = ["Java"]
draft = false
+++

今天看到有一个方式可以把数据库也合并到自动化配置管理之中，其中使用的是
**Liquibase** 这个工具，查了一下文档，发现现在这个工具使用的特别活，今天
也测试了一下，首先是对已经项目生成配置文件，使用下面的 _shell_ 语句：

```shell
liquibase --driver=oracle.jdbc.OracleDriver \
      --classpath=\path\to\classes:jdbcdriver.jar \
      --changeLogFile=com/example/db.changelog.xml \
      --url="jdbc:oracle:thin:@localhost:1521:XE" \
      --username=scott \
      --password=tiger \
      generateChangeLog
```

在 Springboot 中使用 **Liquibase** 需要在 _application.yml_ 文件中增加一
个配置：

```yaml
spring:
  liquibase: classpath:db/changelog/db.changelog-master.xml
```

但是最好的方式是将下面的内容修改，可以将每一个数据库单独拿出来使用。

这个引入的过程中，支持 _xml_ 文件，也支持 _sql_ 、 _json_ 等类型。但是
默认生成的文件是 _xml_ 的。

```xml
<?xml version="1.0" encoding="UTF-8"?>
<databaseChangeLog
    xmlns="http://www.liquibase.org/xml/ns/dbchangelog/1.1"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://www.liquibase.org/xml/ns/dbchangelog/1.1
    http://www.liquibase.org/xml/ns/dbchangelog/dbchangelog-1.1.xsd">
    <include file="db/changelog/db.changelog-1.0.xml"/>
    <include file="db/changelog/db.changelog-1.1.xml"/>
</databaseChangeLog>
```
