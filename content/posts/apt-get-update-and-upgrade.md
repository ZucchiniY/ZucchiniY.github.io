+++
title = "apt-get 中 update 与 upgrade 的区别"
author = ["Dylan Yang"]
date = 2018-08-02T17:14:00+08:00
tags = ["Linux"]
categories = ["笔记"]
draft = false
+++

-   `update` 是更新 **/etc/apt/sources.list** 和 **/etc/apt/sources.list.d**
    中列出的源的地址,这样才能获取到最新的软件包。
-   `upgrade` 是升级已安装的所有软件包，升级之后的版本就是本地地址里的，因此，在执行 **upgrade** 之前一定要执行 **update** , 这样才能更新到最新的。
