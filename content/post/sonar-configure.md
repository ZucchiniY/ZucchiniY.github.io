---
title: "配置 Sonarqube"
date: 2016-11-17T22:10:21+08:00
draft: false
tags: ["Sonarqube","配置"]
categories: ["技术"]
author: "Dylan Yang"
---

# 如何配置 Mac 的环境变量

- 创建一个 =.bash_profile= 文件

``` bash
$ touch ~/.bash_profile
$ vi ~/.bash_profile
```

- 在文件中增加环境变量

``` shell
export PATH="$HOME/usr/local/mysql/bin:$PATH"
```
<!--more-->

- 并使文件中的环境变量生效

``` bash
source ~/.bash_profile
```

# 将 *SONARQUBE* 和 *SONAR_SCANNER* 解压到对应路径

- 修改 Sonar 配置文件
 
  编辑 *<install_directory>/conf/sonar.properties* 文件，配置数据库设置，默认已经提供了数据库的支持，这里使用 mysql，因此取消 mysql 模块的注释。

    ``` bash
    $ vi sonar.properties
    ```

    ``` bash
    sonar.jdbc.username: sonar
    sonar.jdbc.password: sonar
    sonar.jdbc.url jdbc:mysql://localhost:3306/sonar?useUnicode=true&characterEncoding=utf8&rewriteBatchedStatements=true  
    # Optional properties
    sonar.jdbc.driverClassName: com.mysql.jdbc.Driver
    ```
