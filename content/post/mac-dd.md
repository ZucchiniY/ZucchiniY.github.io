---
title: "Mac OS 下 dd 命令"
date: 2018-04-25T22:35:21+08:00
draft: false
tags: ["dd"]
categories: ["技术"]
author: "Dylan Yang"
---

# Mac 下写入命令

- 找出 U 盘挂载位置

``` sh
diskutil list
```

- 将 U 盘移除

``` sh
diskutil unmountDisk /dev/disk[num]
```

- 写入 U 盘

``` sh
sudo dd if=isopath of=/dev/disk[num] bs=1m rdisk
```

`rdisk` 是指定方式后，可以加快写入速度。

<!--more-->
# iso 转换为 dmg

``` sh
sudo hdiutil convert -format UDRW -o linux.dmg kali.iso
```

# 弹出 U 盘

``` sh
diskutil eject /dev/disk[num]
```