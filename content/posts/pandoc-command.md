+++
title = "Pandoc 命令"
author = ["Dylan Yang"]
date = 2016-01-19T17:08:00+08:00
tags = ["pandoc"]
categories = ["笔记"]
draft = false
+++

## org 转换为 docx {#org-转换为-docx}

-   基本命令

<!--listend-->

```shell
pandoc xxx.org -o xxx.docx
```

-   利用 css 进行配置着色

<!--listend-->

```shell
pandoc 01-chapter2.markdown -o chapter2.docx -c Github.css
```


## org 转换为 letex {#org-转换为-letex}

-   使用指定字体

<!--listend-->

```shell
pandoc pandocCh.org -o pandocCh.pdf --latex-engine=xelatex -V mainfont="SimSun"
```

-   使用指定模板

<!--listend-->

```shell
pandoc pandocCh.org -o pandocCh.pdf --latex-engine=xelatex -template=pm-template.latex
```


## org 转换为 html {#org-转换为-html}

```shell
pandoc 01-chapter2.org -o chapter2.html -c Github.css
```


## org 转换为 Markdown {#org-转换为-markdown}

```shell
pandoc -f org -t markdown -o output.md input.org
```
