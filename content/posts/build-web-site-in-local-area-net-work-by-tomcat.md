+++
title = "利用 Tomcat 在局域网建立网页"
author = ["Dylan Yang"]
date = 2016-11-17T11:01:00+08:00
tags = ["tomcat"]
categories = ["前端"]
draft = false
+++

**如何使用 Tomcat 在局域网建立一个网页**


## 配置服务 {#配置服务}


### 下载 {#下载}

首先下载最新的 Tomcat：

[Tomcat 下载地址](http://tomcat.apache.org/download-90.cgi)


## 安装 {#安装}

首先需要安装 appach tomcat，并配置 **conf** 文件夹下的两个文件，
**web.xml** 和 **server.xml**

-   server.xml

    ```xml
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

-   web.xml

    ```xml
    <welcome-file-list>
    <!-- 在此处加上自己定义的起始页 -->
        <welcome-file>sitemap.html</welcome-file>
        <welcome-file>index.html</welcome-file>
        <welcome-file>index.htm</welcome-file>
        <welcome-file>index.jsp</welcome-file>
    </welcome-file-list>
    ```
