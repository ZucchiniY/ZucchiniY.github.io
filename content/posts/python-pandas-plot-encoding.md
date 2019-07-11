+++
title = "Python Pandas 生成图片乱码"
author = ["Dylan Yang"]
date = 2018-09-17T15:18:00+08:00
tags = ["乱码"]
categories = ["Python"]
draft = false
+++

使用 Anaconda 进行数据处理后生成图片的时候，如果不指定对应字体会导致中文乱码，可以通过下面的方案进行解决。

```python
from pylab import mpl
mpl.rcParams['font.sans-serif'] = ['Microsoft YaHei'] # 指定默认字体：解决plot不能显示中文问题
mpl.raParams['axes.unicode_minus'] = False # 解决保存图像是负号'-'显示为方块的问题
```
