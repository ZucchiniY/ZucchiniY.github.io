+++
title = "用 Pandas 进行数据处理系列"
author = ["Dylan Yang"]
date = 2018-09-14T10:57:00+08:00
tags = ["pandas"]
categories = ["Python"]
draft = false
+++

**对某一列数据进行计算**

```python
data['column_name'].value_counts()
```

以之前找到的一个前辈的数据为例子，首先我们要获取文件

```python
import pandas as pd
data = pd.read_excel('xxxx.xls')
```

{{< figure src="/images/pd.png" >}}

这里可以单独查看其中的内容：

```python
data['nick']
```

然后利用一个单独的方法，计算数据量的大小

```python
data['nick'].value_counts()
```

{{< figure src="/images/pd1.png" >}}

同样的情况，我们可以增加分组并获取对应的数据

```python
data1 = data['score'].groupby(data['city'])
data1.mean()
```

这种情况下可以类比为SQL语句：

\#+END\_SRC sql
select avg(score) from data group by city
\#+END\_SRC

{{< figure src="/images/pd2.png" >}}

这样的数据看起来不是特别让人喜欢，这个时间我们可以给他排个序：

```python
data1.mean().sort_values(ascending=False)
```

{{< figure src="/images/pd3.png" >}}

现在看起来好多了，但是有点多了，我们只想看前几条记录：

```python
data1.mean().sort_values(ascending=False).head(3)
```

{{< figure src="/images/pd4.png" >}}

可惜了，好多城市我都没听过，我只想看直辖市的数据

```python
data2 = data.loc[(data['city'].isin(['北京','天津','重庆','上海']))]
```

但是这样还是不特别好看，我们可以再按城市看一下，评分有多少

```python
data2['score'].groupby(data2['city']).mean()
```

这样最终的结果就出来了

{{< figure src="/images/pd5.png" >}}

好了，现在基本的评分我们已经看到了，我希望把这个数据变成图也非常简单：

```python
data3 = data2['score'].groupby(data2['city']).mean()
data3.plot()
```

{{< figure src="/images/pd6.png" >}}

这次先记录到这里，后面会有文章专门写如何出图，也会继续写如何进行数据分析。
