---
title: "apt-get update 与 upgrade 区别"
date: 2018-08-02T21:17:57+08:00
draft: false
tags: ["apt-get update","apt-get upgrade"]
categories: ["技术"]
author: "Dylan Yang"
---

# Debian 的包管理器

- `update` 是更新 *`/etc/apt/sources.list`* 和 *`/etc/apt/sources.list.d`* 中列出的源的地址,这样才能获取到最新的软件包。
- `upgrade` 是升级已安装的所有软件包，升级之后的版本就是本地地址里的，因此，在执行 `upgrade` 之前一定要执行 `update`, 这样才能更新到最新的。

<!--more-->

# 子系统路径

最近在试用 **Windows 10** 下的 **Ubuntu** 子系统，这个系统可以解决一些包的缺失问题，但是有一些工具却是希望使用 **Windows 10** 下的，所以查找了一下所在目录。

`C:\\Users\\用户名\\AppData\\Local\\Packages\\CanonicalGroupLimited.Ubuntu18.04onWindows_79rhkp1fndgsc\\LocalState\\rootfs\\`

上面这个路径相当于 `/` 路径。