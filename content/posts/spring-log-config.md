+++
title = "SpringBoot log 配置"
author = ["Dylan Yang"]
date = 2018-04-24T16:55:00+08:00
tags = ["Springboot", "log"]
categories = ["Java"]
draft = false
+++

-   打印 Mybatis 中调用的 Sql

    ```yml
    logging:
      level:
        com.xxxx.mapper: DEBUG
    ```

**com.xxxx.mapper 是 Mybatis 接口的影射文件包**

-   Logger 日志按级别打印

    ```yml
    logging:
        level:
            org.springframework.web: DEBUG
    ```

其中，日志级别有： **ERROR** **WARN** **INFO** **DEBUG** **TRACE**

-   root 的日志级别设置

    ```yml
    logging:
        level:
            root: DEBUG
    ```
