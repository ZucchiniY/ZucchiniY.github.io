+++
title = "使用 Mac 电脑制作 U 盘"
author = ["Dylan Yang"]
date = 2018-04-25T10:47:00+08:00
tags = ["dd"]
categories = ["笔记"]
draft = false
+++

## Mac 下写入命令 {#mac-下写入命令}

-   找出 U 盘挂载位置

```shell
diskutil list
```

-   将 U 盘移除

```shell
diskutil unmountDisk /dev/disk[num]
```

-   写入 U 盘

```shell
sudo dd if=isopath of=/dev/disk[num] bs=1m rdisk
```

**rdisk** 是指定方式后，可以加快写入速度。


## iso 转换为 dmg {#iso-转换为-dmg}

```shell
sudo hdiutil convert -format UDRW -o linux.dmg kali.iso
```


## 弹出 U 盘 {#弹出-u-盘}

```shell
diskutil eject /dev/disk[num]
```
