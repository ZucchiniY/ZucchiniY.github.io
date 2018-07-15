---
title: "Fedora 修改 user 目录为英文"
date: 2017-07-31T22:10:21+08:00
draft: false
tags: ["Linux","gnome","user home"]
categories: ["Linux"]
author: "Dylan Yang"
---

# 将下载等目录改为英文

这里主要是因为中文在使用 *shell* 的时候并不方便，但是如果系统语言为中文的话这些目录都是中文的。可以使用下面的方法修改为英文。

先将语言修改为英文：

``` sh
# 将语言修改为英文
export LANG=en_US
```
然后更新用户目录：

```shell
# 更新用户目录
xdg-user-dirs-gtk-update
```

这个时候，会提示是否要将用户目录下的文件夹改为英文。选择是，然后再将系统语言刷到中文：

``` sh
# 将语言调为中文
export LANG=zh_CN.UTF-8
```

再执行更新用户目录命令：

```shell
xdg-user-dirs-gtk-update
```

再次输入上面的命令会提示是否改为中文，选择否，并选择不再提醒即可。经过测试这种方法适用于
_GNOME_ 桌面环境。