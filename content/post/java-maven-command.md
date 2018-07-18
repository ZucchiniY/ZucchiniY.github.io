---
title: "Maven Command"
date: 2016-04-27T22:10:21+08:00
draft: false
tags: ["Java","Maven"]
categories: ["Java"]
author: "Dylan Yang"
---

如何使用命令创建一个 Maven 项目。
<!--more-->

# 常用命令
## 创建一个项目

``` sh
mvn archetype:generate -DarchetypeCatalog=internal

-DgroupId=com.mycompany.app -DartifactId=my-app

-DarchetypeArtifactId=maven-archetype-quickstart

-DinteractiveMode=false
```

- mvn archetype:generate 固定格式
- -DgroupId 组织标识，包名
- -DartifactId 项目名称
- -DarchetypeCatalog=internal 不要从远程服务器上取 catalog，解决新建项目卡在 Generating project in interactive mode 处的问题
- -DarchetypeArtifactId 指定 ArchetypeId , maven-archetype-quickstart, 创建一个 java 项目；maven-archetype-webapp，创建一个 web 项目
- -DinteractiveMode 是否使用交互模式

## 编译源代码
``` sh
mvn compile
```

## 编译测试代码
``` sh
mvn test-compile
```

## 清空
``` sh
mvn clean
```

## 运行测试
``` sh
mvn test
```

## 生产站点目录打包
``` sh
mvn site-deploy
```

## 安装当前工程的输出文件到本地仓库
``` sh
mvn install
```

## 打包
``` sh
mvn package
```

## 先清除再打包
``` sh
mvn clean package
```

## 打成 jar 包
``` sh
mvn jar:jar
```

## 生成 eclipse 项目
``` sh
mvn eclipse:eclipse
```

## 查看帮忙信息
``` sh
mvn help:help
```

## 查看 maven 有哪些项目类型分类
``` sh
mvn archetype:generate -DarchetypeCatalog=intrenal
```

## SpringBoot 启动
``` sh
mvn spring-boot:run
```

## 执行 Mybatis-Generator 
``` sh
mvn mybatis-generator:generate -e
```

## 导出对应的 jar 包文件到 lib 目录下
``` sh
mvn dependency:copy-dependencies -DoutputDirectory=lib
```
