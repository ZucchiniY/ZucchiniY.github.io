---
title: "Layui 在表格中实现复选框选择"
date: 2018-05-16T22:10:21+08:00
draft: false
tags: ["Layui","table"]
categories: ["Web"]
author: "Dylan Yang"
---

在 Layui 中实现复选框。
<!--more-->

# 实现

首先要在 **templet** 加上行号数据

``` html
<script type=“text/html” id=“test_id”>
<input type=“checkbox” title=“testbox” id=“id{{d.LAY_TABLE_INDEX}}”>
</script>
```

然后在 **table** 的表头中增加对应的内容

``` html
  table.render({
    cols: [[ //表头
      field: 'test'
      ,title: 'test'
      ,templet: '#test_id'
    ]]
  });
```

然后对数据进行赋值

``` javascript
var data = res.data;
for(var item in data){
$(‘#testbox’ + data[item].LAY_TABLE_INDEX).attr(‘checked’, ‘checked’);
}
form.render();
```
就可以进行渲染了。

# 原理

这主要是因为 **table** 中默认有一个数值，叫 `LAY_TABLE_INDEX` 是用来做为返回的组数据的行号，这里使用这个参数对每一行进行操作，就可以了。