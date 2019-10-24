+++
title = "Python 数据分析初阶"
author = ["Dylan Yang"]
date = 2019-10-18T10:19:00+08:00
draft = true
+++

## 熟悉数据 {#熟悉数据}

| 命令             | 功能                                                                                                                  |
|----------------|---------------------------------------------------------------------------------------------------------------------|
| head             | 预览前 5 行                                                                                                           |
| shape            | 获取数据表的大小                                                                                                      |
| info             | 查看数据类型                                                                                                          |
| describe         | 查看数据分布，包括最大最小值，方差，标准差等                                                                          |
| isnull           | 查看缺失值                                                                                                            |
| dropna           | 删除有缺失值的行，如果只想删除全空的行，使用 dropna(how=all)                                                          |
| fillna           | 将空值补充为 0 ，或者按列进行填充 fillna({'column':'value'})                                                          |
| drop\_duplicates | 删除重复值，默认判断所有值，按某列排序的话，可以使用 drop\_duplicates(subset = 'columns')\\\\ 或者使用多列 drop\_duplicates(subset = ['col1','col2']) |
|                  |                                                                                                                       |
