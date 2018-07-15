---
title: "Emacs 快捷键"
date: 2016-04-26T22:10:21+08:00
draft: false
tags: ["Emacs","Keybinds"]
categories: ["Emacs"]
author: "Dylan Yang"
---

# 设置 Emacs 的默认编码格式

``` emacs
(prefer-coding-system 'utf-8-unix)
```

# 改变文件编码格式

- **C-x C-m f utf-8-unix RET** 将当前文件转换为 *utf-8* 编码
- **C-x C-m c RET C-x C-w RET** 另存为指定编码
  
# 查看需要的库文件

- **M-: image-library-alist RET** 查看 *emacs* 支持需要的库文件

``` text
((xpm "libxpm.dll" "xpm4.dll" "libXpm-nox4.dll")
(png "libpng16.dll" "libpng16-16.dll")
(tiff "libtiff-5.dll" "libtiff3.dll" "libtiff.dll")
(jpeg "libjpeg-9.dll")
(gif "libgif-7.dll")
(svg "librsvg-2-2.dll")
(gdk-pixbuf "libgdk_pixbuf-2.0-0.dll")
(glib "libglib-2.0-0.dll")
(gobject "libgobject-2.0-0.dll")
(gnutls "libgnutls-28.dll" "libgnutls-26.dll")
(libxml2 "libxml2-2.dll" "libxml2.dll")
(zlib "zlib1.dll" "libz-1.dll"))
```
