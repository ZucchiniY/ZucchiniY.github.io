+++
title = "Layui 表格分页"
author = ["Dylan Yang"]
date = 2018-08-02T14:35:00+08:00
tags = ["layui"]
categories = ["前端"]
draft = false
+++

**Layui** 分页是由 **laypage** 实现的，所以既需要分页 **laypage** 还需要数据表格相关的内容。


## 数据表格设置 {#数据表格设置}

```javascript
table.render({
    page: true
    ...
})
```

这样就可以进行分页了，但是如果想要修改分页的样式，可以按下面的方式进行修改：

```javascript
table.render({
    page: {
        layout: ['limit','count','prev','page','next','skip'] // 分页布局
        ,groups: 1 // 只显示1个连续页码
        ,first: false // 不显示首页
        ,last: false // 不显示尾页
        ,theme: '#c00' // 可以传入颜色或者任意普通字符
    }
})
```

其中 _layout_ 中支持数据有：

1.  _count_ 总条目输区域
2.  _prev_ 上一页区域
3.  /page/分页区域
4.  _next_ 下一页区域
5.  _limit_ 条目选项区域
6.  _refresh_ 页面刷新区域
7.  _skip_ 快捷跳页区域
