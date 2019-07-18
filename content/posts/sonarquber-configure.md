+++
title = "配置 SonarQube"
author = ["Dylan Yang"]
date = 2016-11-17T15:03:00+08:00
tags = ["SonarQube"]
categories = ["笔记"]
draft = false
+++

## 如何配置 Mac 的环境变量 {#如何配置-mac-的环境变量}

-   创建一个 `.bash_profile` 文件

    ```shell
    touch ~/.bash_profile
    vi ~/.bash_profile
    ```

-   在文件中增加环境变量

    ```shell
    export PATH="$HOME/usr/local/mysql/bin:$PATH"
    ```

-   并使文件中的环境变量生效

    ```shell
    source ~/.bash_profile
    ```


## 将 **SONARQUBE** 和 **SONAR\_SCANNER** 解压到对应路径 {#将-sonarqube-和-sonar-scanner-解压到对应路径}

-   修改 Sonar 配置文件

    编辑 **<install\_directory>/conf/sonar.properties** 文件，配置数据库设置，默认已经提供了数据库的支持，这里使用 mysql，因此取消 mysql 模块的注释。

    ```shell
    vi sonar.properties
    ```

文件的内容如下：

```shell
sonar.jdbc.username: sonar
sonar.jdbc.password: sonar
sonar.jdbc.url jdbc:mysql://localhost:3306/sonar?useUnicode=true&characterEncoding=utf8&rewriteBatchedStatements=true# Optional properties
sonar.jdbc.driverClassName: com.mysql.jdbc.Driver
```
