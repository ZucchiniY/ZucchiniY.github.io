+++
title = "Matplotlib 学习笔记"
author = ["Dylan Yang"]
date = 2019-07-26T15:41:00+08:00
draft = true
+++

记录了几个好入的可视化库，学习还是要从基础—— Matplotlib 开始学习。


## 图表基本 {#图表基本}

```python
import numpy as np
import matplotlib.pyplot as plt

plt.plot(np.random.rand(10))
# 创建图表
plt.show()
```

{{< figure src="/images/matplotlib01.png" >}}

与 Emacs org mode 交互使用：

```python
import matplotlib.pyplot as plt
import matplotlib
import numpy
matplotlib.use('Agg')

fig = plt.figure(figsize=(4, 2))
x = numpy.linspace(-15, 15)
plt.plot(numpy.sin(x)/x)
fig.tight_layout()
plt.savefig('images/python-matplot-fig.png')
return '/images/python-matplot-fig.png'  # return filename to org-mode
```

{{< figure src="/images/python-matplot-fig.png" >}}

`plt.close()`
: 关闭窗口

`plt.gcf().clear()`
: 每次清空图标内的内容

{{< figure src="/images/matplotlib-anatomy.png" >}}

```python
import pandas as pd
import matplotlib.pyplot as plt
import matplotlib
import numpy as np

df = pd.DataFrame(np.random.rand(10, 2), columns=['A', 'B'])
f = plt.figure(figsize=(10, 10))
fig = df.plot(figsize=(8, 6))

# 表头
plt.title('aa')
plt.xlabel('x')
plt.xlabel('y')

# 图例位置
# best 自适应位置
# upper right
# upper left
# lower left
# lower right
# right
# center left
# center right
# lower center
# upper center
# center
plt.legend(loc='best')

# x 轴边界
plt.xlim([0, 10])
# y 轴边界
plt.ylim([0, 1.1])
# 设置 x 刻度
plt.xticks(range(10))
# 设置 y 刻度
plt.yticks([0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.2])
# x 轴刻度标签
fig.set_xticklabels('%.1f' % i for i in range(10))
# y 轴刻度标签
fig.set_yticklabels('%.2f' % i for i in [0, 0.2, 0.4, 0.6, 0.8, 1.0, 1.2])
# 边界限定了值的范围，刻度表示显示的标尺，这里 x 轴是 0 - 10 ，但是刻度只有 0.0 - 9.0
plt.savefig('./images/matplotlib02.png')
return '/images/matplotlib02.png'
```

{{< figure src="/images/matplotlib02.png" >}}

-   图表基本样式

```python
import numpy as np
import matplotlib.pyplot as plt
import matplotlib

x = np.linspace(-np.pi,np.pi ,256, endpoint=True)
c, s = np.cos(x), np.sin(x)

plt.plot(c)
plt.plot(s)

# 显示网格
# linestyle: 线型
# color: 颜色
# linewidth: 宽度
# axis: x,y,both 显示 x,y,两者
plt.grid(True, linestyle='--', color='gray', linewidth='0.5', axis='both')
plt.tick_params(bottom='on', top='on', left='on',right='on')
# 显示刻度的方向 in, out, inout
matplotlib.rcParams['xtick.direction']='out'
matplotlib.rcParams['ytick.direction']='in'
# 返回当前 axes 对象，gcf() 返回当前 figure 对象
frame = plt.gca()
plt.axis('on')
frame.axes.get_xaxis().set_visible(True)
frame.axes.get_yaxis().set_visible(False)

plt.savefig('./images/matplotlib03.png')
return '/images/matplotlib03.png'
```

{{< figure src="/images/matplotlib03.png" >}}

-   线样式
    -   **'-':** 直线
    -   **'--':** 虚线
    -   **'-.':** 点横线
    -   **':':** 全点线


## 子图 {#子图}

在 matplotlib 中，整个图像为 Figure ，而一个 Figure 中可以有多个 axes。

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import matplotlib
matplotlib.style.use('bmh')

fig = plt.figure(figsize=(10, 6), facecolor='gray')
# 创建图表，在2行2列的第一个位置
ax1 = fig.add_subplot(2, 2, 1)
plt.plot(np.random.rand(50).cumsum(), '--g')

ax2 = fig.add_subplot(2, 2, 4)
ax2.hist(np.random.rand(50).cumsum(), alpha=0.5, color='b')

ax4 = fig.add_subplot(2, 2, 2)
df2 = pd.DataFrame(np.random.rand(10, 4), columns=['a', 'b', 'c', 'd'])
ax4.plot(df2, linestyle='--', marker='.')
plt.savefig('./images/matplotlib04.png')
return '/images/matplotlib04.png'
```

{{< figure src="/images/matplotlib04.png" >}}

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import matplotlib

df = pd.DataFrame(np.random.randn(1000, 4), columns=list('ABCD'))
df = df.cumsum()

df.plot(style='--', alpha=0.5, grid=True,
        figsize=(8, 6), subplots=True, layout=(2, 2))
plt.subplots_adjust(wspace=0, hspace=0.2)
plt.savefig('./images/matplotlib05.png')
return '/images/matplotlib05.png'
```

{{< figure src="/images/matplotlib05.png" >}}

-   Series 直接生成图表

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import matplotlib

ts = pd.Series(np.random.randn(12),
               index=pd.date_range('1/1/2019', periods=12))
ts = ts.cumsum()

ts.plot(
    # kind 包括，line, bar, barh
    kind='line',
    color='r',
    # linestyle -, marker . color g
    style='-gx',
    # alpha 透明度，0-1
    alpha=0.5,
    use_index=True,
    rot=0,
    ylim=[-50, 50],
    yticks=list(range(-50, 50, 10)),
    title='Time Series',
    legend=True,
    label='test')
plt.grid(True, linestyle=':', color='gray', linewidth='0.5', axis='both')

plt.savefig('./images/matplotlib06.png')
return '/images/matplotlib06.png'
```

{{< figure src="/images/matplotlib06.png" >}}

-   Dataframe 直接生成图表

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import matplotlib

df = pd.DataFrame(np.random.randn(12, 4),
                  index=pd.date_range('1/1/2019', periods=12), columns=list('abcd'))
df = df.cumsum()
df.plot(
    style='--.',
    alpha=0.8,
    ylim=[-100, 100],
    figsize=(10, 8),
    grid=True,
    yticks=list(range(-100, 125, 25)),
    title='test',
    subplots=True)
plt.grid(True, linestyle=':', color='gray', linewidth='0.5', axis='both')

plt.savefig('./images/matplotlib07.png')
return '/images/matplotlib07.png'
```

{{< figure src="/images/matplotlib07.png" >}}

-   柱关图与堆叠图

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import matplotlib

fig, axes = plt.subplots(4,1, figsize=(12,12))
s = pd.Series(np.random.randint(0,10,16), index=list('abcdefghijklmnop'))
df=pd.DataFrame(np.random.rand(10,3), columns=list('ABC'))

# 单系列柱状图
s.plot(kind='bar', ax=axes[0], grid=True,legend=True,label='s',alpha=0.6)

# 多系列柱状图
df.plot(kind='bar',ax=axes[1],colormap='Reds_r')

# 多系列堆叠图
df.plot(kind='bar',ax=axes[2], colormap='Blues_r', stacked=True)

df.plot.barh(ax=axes[3],grid=True,stacked=True,colormap='BuGn_r')

plt.savefig('./images/matplotlib08.png')
return '/images/matplotlib08.png'
```

{{< figure src="/images/matplotlib08.png" >}}

-   柱状图

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import matplotlib

plt.figure(figsize=(10, 4))
x = np.arange(10)
y1 = np.random.rand(10)
y2 = np.random.rand(10)
plt.bar(x, y1, width=0.8, facecolor='green', edgecolor='black', yerr=y1*0.1)
plt.bar(x, -y2, width=0.8, facecolor='yellow', edgecolor='black', yerr=y2*0.1)
for i, j in zip(x, y1):
    plt.text(i-0.2, j+0.1, '%.2f' % j, color='blue')

for i, j in zip(x, y2):
    plt.text(i, -j-0.2, '%.2f' % j, color='blue')

plt.savefig('./images/matplotlib09.png')
return '/images/matplotlib09.png'
```

{{< figure src="/images/matplotlib09.png" >}}
