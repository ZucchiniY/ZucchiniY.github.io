+++
title = "用 Pandas 进行数据处理系列 二"
author = ["Dylan Yang"]
date = 2019-07-31T16:11:00+08:00
tags = ["pandas"]
categories = ["Python"]
draft = false
+++

## 获取指定的列和行 {#获取指定的列和行}

```python
import pandas as pd

df = pd.read_csv('xxxx.xls')
```

获取行操作
: `df.loc[3:6]`

获取列操作
: `df['rowname']`

取两列
: `df[['a_name','bname']]` ，里面需要是一个 list 不然会报错

增加一列
: `df['new']=list([...])`

对某一列除以他的最大值
: `df['a']/df['a'].max()`

排序某一列
: `df.sorted_values('a',inplace=True,ascending=True)` ，
    inplace 表示排序的时候是否生成一个新的 dataFrame ，
    ascending=True 表示升序，默认为升序，如果存在缺失的补值（ _Nan_ )，排序的时候会将其排在末尾


## 基本用法 {#基本用法}


### 数据表信息查看 {#数据表信息查看}

df.shape
: 维度查看

df.info()
: 数据表基本信息，包括围度、列名、数据格式、所占空间

df.dtypes
: 每一列的数据格式

df['b'].dtype
: 某一列的格式

df.isnull()
: 是否空值

df.['b'].unique()
: 查看某一列的唯一值

df.values
: 查看数据表的值

df.columns
: 查看列名

df.head()
: 查看默认的前 10 行数据

df.tail()
: 查看默认的后 10 行数据


### 数据表清洗 - df.fillna(value=0) :: 用数字 0 填充空值 {#数据表清洗-df-dot-fillna--value-0--用数字-0-填充空值}

df['pr'].fillna(df['pr'].mean())
: 用列 pr 的平均值对 na 进行填充

df['city']=df['city'].map(str.strip)
: 清除 city 字段的字符空格

df['city']=df['city'].str.lower()
: 大小写转换

df['pr'].astype('int')
: 更改数据的格式

df.rename(columns={'category': 'category-size'})
: 更改列名

df['city'].drop\_duplicates()
: 删除后出现的重复值

df['city'].drop\_duplicates(keep='last')
: 删除先出现的重复值

df['city'].replace('sh', 'shanghai')
: 数据替换


### 数据预处理 {#数据预处理}

-   数据表合并

    ```python
    df_inner = pd.merge(df, df1, how='inner')  # 匹配合并，交集
    df_left = pd.merge(df, df1, how='left')  # 左联表
    df_right = pd.merge(df, df1, how='right')  # 右联表
    df_outer = pd.merge(df, df1, how='outer')  # 并集
    ```

-   设置索引列

<!--listend-->

```python
df.set_index('id')
```

-   按照特定列的值排序

<!--listend-->

```python
df.sort_values(by=['age'])
```

-   按照索引列排序

<!--listend-->

```python
df.sort_index()
```

-   如果 pr 列的值大于 3000 ， group 列显示 hight , 否则显示 low

<!--listend-->

```python
df['group'] = np.where(df['pr'] > 3000, 'hight', 'low')
```

-   对复合多个条件的数据进行分级标记

<!--listend-->

```python
df.loc[(df['city'] == 'beijing') & (df['pr'] >= 4000), 'sign'] = 1
```

-   对 category 字段的值依次进行分列，并创建数据表，索引值 df 的索引列，列名称为 category 和 size

<!--listend-->

```python
pd.DataFrame((x.split('-')
              for x in df['category']), index=df.index, columns=['category', 'size'])
```


### 数据提取 {#数据提取}

主要用到三个函数， `loc` , `iloc` , `ix` 。

loc
: 函数按标签值进行提取

iloc
: 按位置进行提取

ix
: 可以同时按标签和位置进行提取

具体的使用见下：

df.loc[3]
: 按索引提取单行的数值

df.iloc[0:5]
: 按索引提取区域行数据值

df.reset\_index()
: 重设索引

df=df.set\_index('date')
: 设置 date 为索引

df[:'2013']
: 提取 2013 之前的所有数据

df.iloc[:3,:2]
: 从 0 位置开始，前三行，前两列，这里的数据不同去是索引的标签名称，而是数据所有的位置

df.iloc[[0,2,5],[4,5]]
: 提取第 0、2、5 行，第 4、5 列的数据

df.ix[:'2013',:4]
: 提取 2013 之前，前四列数据

df['city'].isin(['beijing'])
: 判断 city 的值是否为北京

df.loc[df['city'].isin(['beijing','shanghai'])]
: 判断 city 列里是否包含 beijing 和 shanghai ，然后将符合条件的数据提取出来

pd.DataFrame(category.str[:3])
: 提取前三个字符，并生成数据表


### 数据筛选 {#数据筛选}

使用与、或、非三个条件配合大于、小于、等于对数据进行筛选，并进行计数和求和。

-   使用与进行筛选

<!--listend-->

```python
df.loc[(df['age'] > 25) & (df['city'] == 'beijing'),
       ['id', 'city', 'age', 'category']]
```

-   使用或进行筛选

<!--listend-->

```python
df.loc[(df['age'] > 25) | (df['city'] == 'beijing'), ['id', 'city', 'age']]
```

-   使用非进行筛选

<!--listend-->

```python
df.loc[(df['city'] != 'beijing'), ['id', 'city', 'age']].sort(['id'])
```

-   筛选后的灵气按 city 列进行计数

<!--listend-->

```python
df.loc[(df['city'] != 'beijing'), ['id', 'city', 'age']].sort(
    ['id']).city.count()
```

-   使用 query 函数进行筛选

<!--listend-->

```python
df.query('city' == ['beijing', 'shanghai'])
```

-   对筛选后的结果按 pr 进行求和

<!--listend-->

```python
df.query('city' == ['beijing', 'shanghai']).pr.sum()
```


### 数据汇总 {#数据汇总}

主要使用 groupby 和 pivote\_table 进行处理。

df.groupby('city').count()
: 按 city 列分组后进行数据汇总

df.groupby('city')['id'].count()
: 按 city 进行分组，然后汇总 id 列的数据

df.groupby(['city','size'])['id'].count()
: 对两个字段进行分组汇总，然后进行计算

df.groupby('city')['pr'].agg([len, np.sum,np.mean])
: 对 city 进行分组，然后计算 pr 列的大小、总和和平均数


### 数据统计 {#数据统计}

数据采样，计算标准差、协方差和相关系数。

-   简单数据采样

<!--listend-->

```python
df.sample(n=3)
```

-   手动设置采样权重

<!--listend-->

```python
weights = [0, 0, 0, 0, 0, 0.5, 0.5]
df.sample(n=2, weights=weights)
```

-   采样后不放回

<!--listend-->

```python
df.sample(n=6, replace=False) # 如果 replace = True 采样后放回
```

-   数据表描述性统计

<!--listend-->

```python
df.describe().round(2).T  # round 表示显示的小数位数，T 表示转置
```

-   计算列的标准差

<!--listend-->

```python
df['pr'].std()
```

-   计算两个字段间的协方差

<!--listend-->

```python
df['pr'].cov(df['m-point'])
```

-   计算表中所有字段间的协方差

<!--listend-->

```python
df.cov()
```

-   两个字段间的相关性分析

<!--listend-->

```python
df['pr'].corr(df['m-point'])  # 相关系数在 [-1, 1] 之间，接近 -1 为负相关，1 为正相关，0 为不相关
```

-   数据表的相关性分析

<!--listend-->

```python
df.corr()
```


## 数据分组与聚合实践 {#数据分组与聚合实践}

```python
import pandas as pd

df = pd.DataFrame({'Country': ['China', 'China', 'India', 'India', 'America', 'Japan', 'China', 'India'],
                   'Income': [10000, 10000, 5000, 5002, 40000, 50000, 8000, 5000],
                   'Age': [5000, 4321, 1234, 4010, 250, 250, 4500, 4321]})
print(df)
```

-   分组

<!--listend-->

```python
import pandas as pd

df = pd.DataFrame({'Country': ['China', 'China', 'India', 'India', 'America', 'Japan', 'China', 'India'],
                   'Income': [10000, 10000, 5000, 5002, 40000, 50000, 8000, 5000],
                   'Age': [5000, 4321, 1234, 4010, 250, 250, 4500, 4321]})
df_gb = df.groupby('Country')
for index, data in df_gb:
    print(index)
    print(data)
```

多列分组

```python
import pandas as pd

df = pd.DataFrame({'Country': ['China', 'China', 'India', 'India', 'America', 'Japan', 'China', 'India'],
                   'Income': [10000, 10000, 5000, 5002, 40000, 50000, 8000, 5000],
                   'Age': [5000, 4321, 1234, 4010, 250, 250, 4500, 4321]})
df_gb = df.groupby([ 'Country','Income' ])
for (index1,index2), data in df_gb:
    print((index1,index2))
    print(data)
```

-   聚合

对分组后的数据进行聚合

```python
import pandas as pd

df = pd.DataFrame({'Country': ['China', 'China', 'India', 'India', 'America', 'Japan', 'China', 'India'],
                   'Income': [10000, 10000, 5000, 5002, 40000, 50000, 8000, 5000],
                   'Age': [5000, 4321, 1234, 4010, 250, 250, 4500, 4321]})
df_agg = df.groupby('Country').agg(['min', 'mean', 'max'])
print(df_agg)
```

对分组后的部分列进行聚合

```python
import pandas as pd

df = pd.DataFrame({'Country': ['China', 'China', 'India', 'India', 'America', 'Japan', 'China', 'India'],
                   'Income': [10000, 10000, 5000, 5002, 40000, 50000, 8000, 5000],
                   'Age': [5000, 4321, 1234, 4010, 250, 250, 4500, 4321]})

num_agg = {'Age': ['min', 'mean', 'max']}
print(df.groupby('Country').agg(num_agg))
```

```python
import pandas as pd

df = pd.DataFrame({'Country': ['China', 'China', 'India', 'India', 'America', 'Japan', 'China', 'India'],
                   'Income': [10000, 10000, 5000, 5002, 40000, 50000, 8000, 5000],
                   'Age': [5000, 4321, 1234, 4010, 250, 250, 4500, 4321]})

num_agg = {'Age': ['min', 'mean', 'max'], 'Income':['min','max']}
print(df.groupby('Country').agg(num_agg))
```


### 补充 {#补充}

对于聚合方法的传入和传出，可以使用 `['min']` ，也可以使用 numpy 中的方法，比如 `numpy.min` ，也可以传入一个方法，比如：

```python
def max_deviation(s):
    std_score = (s - s.mean()) / s.std()
    return std_score.abs().max()


df.groupby('ss').agg(max_deviation).round(1).head()
```

对于聚合后的数据表格，是多级索引，可以重新定义索引的数据

```python
import pandas as pd

df = pd.DataFrame({'Country': ['China', 'China', 'India', 'India', 'America', 'Japan', 'China', 'India'],
                   'Income': [10000, 10000, 5000, 5002, 40000, 50000, 8000, 5000],
                   'Age': [5000, 4321, 1234, 4010, 250, 250, 4500, 4321]})

num_agg = {'Age': ['min', 'mean', 'max'], 'Income': ['min', 'max']}
ss = df.groupby('Country').agg(num_agg)
l0 = ss.columns.get_level_values(0)
print(l0)
l1 = ss.columns.get_level_values(1)
print(l1)
ss.columns = l0 + '_' + l1
print(ss)

ss.reset_index()
print(ss)
```

pandas 默认会将分组后将所有分组列放在索引中，但是可以使用
as\_index=False 来避免这样。

```python
import pandas as pd

df = pd.DataFrame({'Country': ['China', 'China', 'India', 'India', 'America', 'Japan', 'China', 'India'],
                   'Income': [10000, 10000, 5000, 5002, 40000, 50000, 8000, 5000],
                   'Age': [5000, 4321, 1234, 4010, 250, 250, 4500, 4321]})

num_agg = {'Age': ['min', 'mean', 'max'], 'Income': ['min', 'max']}
ss = df.groupby(['Country'], as_index=False).agg(num_agg)
print(ss)
```


### appy 用法 {#appy-用法}

```python
import pandas as pd

df = pd.DataFrame([[4, 9], ]*3, columns=list('AB'))
print(df)
```

```python
import pandas as pd
import numpy as np

df = pd.DataFrame([[4, 9], ]*3, columns=list('AB'))

print(df.apply(np.sqrt))
```

```python
import pandas as pd
import numpy as np

df = pd.DataFrame([[4, 9], ]*3, columns=list('AB'))

print(df.apply(np.sum, axis=0))
```

```python
import pandas as pd
import numpy as np

df = pd.DataFrame([[4, 9], ]*3, columns=list('AB'))

print(df.apply(lambda x: [1, 2], axis=1))
```

result\_type='expand' 的时候，可以将结果扩展为列表。

```python
import pandas as pd
import numpy as np

df = pd.DataFrame([[4, 9], ]*3, columns=list('AB'))

print(df.apply(lambda x: [1, 2], axis=1, result_type='expand'))
```

```python
import pandas as pd
import numpy as np

df = pd.DataFrame([[4, 9], ]*3, columns=list('AB'))

print(df.apply(lambda x: pd.Series([1, 2], index=['foo', 'bar']), axis=1))
```

```python
import pandas as pd
import numpy as np

df = pd.DataFrame([[4, 9], ]*3, columns=list('AB'))

print(df.apply(lambda x: [1, 2], axis=1, result_type='broadcast'))
```

```python
import pandas as pd
import numpy as np

df = pd.DataFrame([[4, 9], ]*3, columns=list('AB'))

print(df.applymap(lambda x: x**2))
```
