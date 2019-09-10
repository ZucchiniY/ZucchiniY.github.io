+++
title = "自动化生成报表"
author = ["Dylan Yang"]
date = 2019-08-09T14:53:00+08:00
tags = ["透视表"]
categories = ["Python"]
draft = false
+++

-   利用 `read_excel()` 的 **usecols** 参数对表进行指定，排除不必要的干扰列
-   养成数据加载以后，使用 `head()` 进行预览的习惯
-   养成使用 `shape` 及 `info()` 了解表格基本情况的习惯

利用 `info()` 方法查看数据中是否有空值，如果有空值的话，则可以使用
`dropna()` 方法将其移除。

需要掌握的主要有两个方法，一个是 `DataFrame.insert()` 方法，用来增加对应的列，另一个是 `DataFrame.pivot_table()` 方法。

-   insert()

    DataFrame.insert(self, loc, column, value, allow\_duplicates=False)

    loc : int 表示第几列；0 <= loc <= len(columns)
    column : string, number, or hashable object;给插入的列取名，如 column='新的一列'
    value : int ，array，series
    allow\_duplicates : bool 是否允许列名重复，选择 True 表示允许新的列名与已存在的列名重复。

-   pivot\_table()

DataFrame.pivot\_table(self, values=None, index=None, columns=None, aggfunc='mean', fill\_value=None, margins=False, dropna=True, margins\_name='All', observed=False)

values : 要进行透视展示的数据
index : 需要重新进行展示成列，是原始数据中的某一个行
columns : 要重新展示为行的内容，是原来的列或者是其它的属性，可以是列表
aggfunc : 要进行统计的行，可以是 `numpy.sum` / `numpy.mean` 等，也可以按列进行统计 `aggfunc={'c1' : numpy.mean, 'c2' : numpy.sum}`
fill\_value : 将缺失值替换的值，幽灵将 Nan 换成 0 : `fill_value=0`
margins : bool, 增加行或者列的汇总信息
dropna : bool ，是否要删除为空的信息
margin\_name : string , 默认为 all ，或者自定义一个名称
observed bool , True 显示分类中的数据，False 显示所有数据，默认为 False

```python
import pandas as pd
from datetime import datetime

data = pd.read_excel(r'~/workspace/code/python/excel-python/python_learning.xlsx',
                     usecols=[1, 4, 6, 7, 8, 9, 10, 11, 12], sheet_name='个人贷款客户信息表')
data = data[data['合同生效日'] > datetime(2018, 12, 31)]

# 按逻辑，将一组数据拆成三组
data1 = data[["用途", "贷款金额", "单位1", "分成比例1"]]
data2 = data[["用途", "贷款金额", "单位2", "分成比例2"]]
data3 = data[["用途", "贷款金额", "单位3", "分成比例3"]]

# 将三组内容，重新命名之后合成一个新表
data1 = data1.rename(columns={"单位1": "单位", "分成比例1": "分成比例"})
data2 = data2.rename(columns={"单位2": "单位", "分成比例2": "分成比例"})
data3 = data3.rename(columns={"单位3": "单位", "分成比例3": "分成比例"})

data4 = pd.concat([data1, data2, data3], ignore_index=True)

# 将数据中的空值清除
data4 = data4.dropna()

# 插入新的数据
# 1. insert() 方法
data4.insert(2, "分成百分比", data4["分成比例"]/100)
data4.insert(5, "分成贷款金额", data4["贷款金额"]*data4["分成百分比"]/10000, False)
# 普通索引方式插入
# data4["分成贷款金额"] = data4["贷款金额"]*data4["分成百分比"]/10000

# 增加数据透视
data5 = data4[['单位', '用途', '分成贷款金额']]
data6 = pd.pivot_table(data5, values="分成贷款金额", columns="用途", index="单位",
                       aggfunc='sum', fill_value=0, observed=False).reset_index()
print(data6.head())
```
