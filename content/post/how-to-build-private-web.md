---
title: "如何搭建私有网站"
date: 2016-11-17T22:10:21+08:00
draft: false
tags: ["Tomcat","局域网"]
categories: ["Web"]
author: "Dylan Yang"
---

如何在本地环境下用 tomcat 打造一个个人网站。
<!--more-->

# 配置服务

## 下载

首先下载最新的 Tomcat：

``` xml
http://tomcat.apache.org/download-90.cgi
```

# 安装

首先需要安装 appach tomcat，并配置 _/conf_ 下的两个文件，*web.xml* 和 *server.xml*

- server.xml

``` html
<Host name="localhost" appBase="D:\org" <!-- 配置主目录，然后所有的网站都可以放在此目录下-->
    unpackWARs="true" autoDeploy="true">

    <!-- SingleSignOn valve, share authentication between web applications
     Documentation at: /docs/config/valve.html -->
    <!--
<Valve className="org.apache.catalina.authenticator.SingleSignOn" />
-->
    <!-- 增加下面的目录，可以访问 -->
    <Context path="/wiki" docBase="/public_html" debug="0" reloadable="true" />

    <!-- Access log processes all example.
     Documentation at: /docs/config/valve.html
     Note: The pattern used is equivalent to using pattern="common" -->
    <Valve className="org.apache.catalina.valves.AccessLogValve" directory="logs" prefix="localhost_access_log." suffix=".txt"
        pattern="%h %l %u %t &quot;%r&quot; %s %b" />
</Host>
```

- web.xml

``` html
<welcome-file-list>
<!-- 在此处加上自己定义的起始页 -->
    <welcome-file>sitemap.html</welcome-file>
    <welcome-file>index.html</welcome-file>
    <welcome-file>index.htm</welcome-file>
    <welcome-file>index.jsp</welcome-file>
</welcome-file-list>
```
