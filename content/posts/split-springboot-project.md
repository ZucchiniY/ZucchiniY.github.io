+++
title = "拆分 SpringBoot 项目"
author = ["Dylan Yang"]
date = 2019-05-09T15:40:00+08:00
tags = ["SpringBoot"]
categories = ["Java"]
draft = false
+++

最近发现使用 Springboot 项目上传到服务器越来越慢，所以决定将项目拆分一下，将需要的 _lib_ 包拆分开来。

首先需要按原来的内容进行打包，然后就打好的包解压，然后将 **BOOT-INF** 下的内容，上传到服务器，然后将 _pom.xml_ 文件中的
**org.springframework.boot** 增加 **configuration** 的配置，增加之后如下：

```xml
<plugin>
  <groupId>org.springframework.boot</groupId>
  <artifactId>spring-boot-maven-plugin</artifactId>
  <configuration>
    <layout>ZIP</layout>
    <includes>
      <include>
        <groupId>nothing</groupId>
        <artifactId>nothing</artifactId>
      </include>
    </includes>
  </configuration>
</plugin>
```

然后再重新打包，生成的内容就只有自己编写的内容了。

上传到服务器之后，先新建一个 **shell** 角本，然后增加执行权限： `chmod
x+a start.sh` 然后将启动的脚本增加如果下内容：

```text
nohup java -Dloader.path=./lib -jar ./springboot.jar &
```

再启动的时候，更新了代码，打包再上传服务器，也就一分钟的事儿。

Archived entries from file /Users/zucchini/workspace/org/blog/hugo-posts.org
