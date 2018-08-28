---
title: "dot 代码实例"
date: 2016-01-08T22:10:21+08:00
draft: false
tags: ["dot","Org mode"]
categories: ["技术"]
author: "Dylan Yang"
---

# Graphviz dot

## Dot 生成图的默认命令

`dot -T<type> -o <outfile> <infile.dot>`

dot 可以替换为circo等其他算法，详细见[命令的选择](#命令的选择)章节。

输入文件是<infile.dot>，生成的格式由<type>指定，生成的文件是<outfile>。
其中-T<type>包括：

``` sh
-Tps (PostScript)
-Tsvg -Tsvgz (Structured Vector Graphics)
-Tfig (XFIG  graphics)
-Tmif  (FrameMaker graphics)
-Thpgl (HP pen plotters)
-Tpcl (Laserjet printers)
-Tpng -Tgif (bitmap graphics)
-Tdia (GTK+ based diagrams)
-Timap (imagemap files for httpd servers for each node or edge  that  has a non-null "href" attribute.)
-Tcmapx (client-side imagemap for use in html and xhtml)
```

## rank

rank 约束了子图的节点位置，有向图中，一个箭头的指向，带有级别，一般是
尾端高于尖端，即 `a->b` a 的级别要高于 b 的级别。

- same : 所有节点在同一级别的节点处
- min : 所有节点在最小级别节点处
- source : 所有节点在最低级别，且只有子图属性为 *source* 或者 *min* 的时候，才能使用同样的级别
- max : 类似于 *source*
- sink : 类似于 *source*
 
> *NOTE:* 最低级别，可以是 *最上* 、*最下* 、*最左* 、*最右* 

## rankdir
- TB : top-to-bottom
- LR : left-to-right
- BT : bottom-to-top
- RL : right-to-left

## dot 线条

``` md
splines = ortho #直角拆线
splines = spline #曲线（不遮挡）
splines = cuvved #曲线（可遮挡）
splines = line #直线（可遮挡）
splines = polyline #直线（不遮挡）
```

## 命令的选择

|命令|介绍|
|---|----|
|dot|渲染图具有明确的方向性|
|neato|图缺乏方向性|
|twopi|图采用放射性布局|
|circo|图采用环形布局|
|fdp|图缺乏方向性|
|sfdp|用来渲染大型图，且图片缺乏方向性|

## 静默执行代码

``` emacs-lisp
#+BEGIN_SRC emacs-lisp
(setq org-confirm-babel-evaluate nil) ;;执行静默语句块
#+END_SRC
```

## dot 实例

- 語言可以用來繪製流程圖,如下:

``` md
 #+BEGIN_SRC dot :file ../images/dot04.png :cmdline -Kdot -Tpng
   digraph structs {
    node[shape=record]
    struct1 [label="<f0> left|<f1> mid\ dle|<f2> right"];
    struct2 [label="{<f0> one|<f1> two\n\n\n}" shape=Mrecord];
    struct3 [label="hello\nworld |{ b |{c|<here> d|e}| f}| g | h"];
    struct1:f1 -> struct2:f0;
    struct1:f0 -> struct3:f1;
   }
#+END_SRC 
```

![](/images/dot04.png)

``` md
#+BEGIN_SRC dot :file ../images/dot01.png :cmdline -Kdot -Tpng
  digraph G {
  size="8,6"
  ratio=expand
  edge [dir=both]
  plcnet [shape=box, label="PLC Network"]
  subgraph cluster_wrapline {
    label="Wrapline Control System"
    color=purple
    subgraph {
    rank=same
    exec
    sharedmem [style=filled, fillcolor=lightgrey, shape=box]
    }
    edge[style=dotted, dir=none]
    exec -> opserver
    exec -> db
    plc -> exec
    edge [style=line, dir=both]
    exec -> sharedmem
    sharedmem -> db
    plc -> sharedmem
    sharedmem -> opserver
  }
  plcnet -> plc [constraint=false]
  millwide [shape=box, label="Millwide System"]
  db -> millwide
  subgraph cluster_opclients {
    color=blue
    label="Operator Client"
    rankdir=LR
    labelloc=b
    node[label=client]
    opserver -> client1
    opserver -> client2
    opserver -> client3
  }
}
#+end_src 
```

![](/images/dot01.png)

``` md
#+BEGIN_SRC dot :file ../images/dot_html01.png :cmdline -Kdot -Tpng
  digraph G {
  rankdir=LR
  node [shape=plaintext]
  a [
     label=<
<TABLE BORDER="0" CELLBORDER="1" CELLSPACING="0">
  <TR><TD ROWSPAN="3" BGCOLOR="yellow">class</TD></TR>
  <TR><TD PORT="here" BGCOLOR="lightblue">qualifier</TD></TR>
</TABLE>>
  ]
    b [shape=ellipse style=filled
  label=<
<TABLE BGCOLOR="bisque">
  <TR><TD COLSPAN="3">elephant</TD> 
      <TD ROWSPAN="2" BGCOLOR="chartreuse" 
          VALIGN="bottom" ALIGN="right">two</TD> </TR>
  <TR><TD COLSPAN="2" ROWSPAN="2">
        <TABLE BGCOLOR="grey">
          <TR> <TD>corn</TD> </TR> 
          <TR> <TD BGCOLOR="yellow">c</TD> </TR> 
          <TR> <TD>f</TD> </TR> 
        </TABLE> </TD>
      <TD BGCOLOR="white">penguin</TD> 
  </TR> 
  <TR> <TD COLSPAN="2" BORDER="4" ALIGN="right" PORT="there">4</TD> </TR>
</TABLE>>
  ]
  c [ 
  label=<long line 1<BR/>line 2<BR ALIGN="LEFT"/>line 3<BR ALIGN="RIGHT"/>>
  ]
  subgraph { rank=same b c }
  a:here -> b:there [dir=both arrowtail = diamond]
  c -> b
  d [shape=triangle]
  d -> c [label=<
<TABLE>
  <TR><TD BGCOLOR="red" WIDTH="10"> </TD>
      <TD>Edge labels<BR/>also</TD>
      <TD BGCOLOR="blue" WIDTH="10"> </TD>
  </TR>
</TABLE>>
  ]
  
  }
  #+END_SRC 
```

![](/images/dot_html01.png)
