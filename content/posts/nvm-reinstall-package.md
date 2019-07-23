+++
title = "nvm 安装最新 nodejs 时重装 package"
author = ["Dylan Yang"]
date = 2018-04-22T14:38:00+08:00
tags = ["nvm"]
categories = ["前端"]
draft = false
+++

-   更新新的node版本，将旧版本模块全部同步安装到新版本下，可以使用下面的命令:

    ```shell
    nvm install node --reinstall-packages-from=node
    ```
