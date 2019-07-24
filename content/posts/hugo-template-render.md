+++
title = "Hugo 渲染模板顺序"
author = ["Dylan Yang"]
date = 2018-08-29T09:37:00+08:00
tags = ["hugo", "render"]
categories = ["笔记"]
draft = false
+++

**hugo** 对网页进行渲染时，是按照先选择目录下再选择主题下的基础模板，具体如下图：

{{< figure src="../images/hugo-template-render.png" >}}

对布局的渲染是按照各自的模板进行选择的，一般是先优先 **Layouts** 路径下的，然后选择对应类型下的路径，如对于 **single page** 是先选择
**layouts/posts/single.html.html** ，然后选择
**layouts/posts/single.html** ，再然后选择
**layouts/\_default/single.html.html** ，最后选择
**layouts/\_default/single.html** 。

具体的渲染方式见 [Hugo官方网站](https://gohugo.io/templates/lookup-order/) 。
