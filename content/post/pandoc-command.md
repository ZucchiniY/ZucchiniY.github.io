---
title: "Pandoc 命令"
date: 2016-01-19T22:10:21+08:00
draft: false
tags: ["Pandoc"]
categories: ["Pandoc"]
description: "Org 使用 Pandoc 进行格式转换"
author: "Dylan Yang"
---

# org 转换为 docx
- 基本命令
``` sh
pandoc xxx.org -o xxx.docx
```
- 利用 css 进行配置着色
``` sh
pandoc 01-chapter2.markdown -o chapter2.docx -c Github.css
```
# org 转换为 letex
- 使用指定字体
``` sh
pandoc pandocCh.org -o pandocCh.pdf --latex-engine=xelatex -V mainfont="SimSun"
```
<!--more-->

- 使用指定模板
``` sh
pandoc pandocCh.org -o pandocCh.pdf --latex-engine=xelatex -template=pm-template.latex
```
# org 转换为 html
``` sh
pandoc 01-chapter2.org -o chapter2.html -c Github.css
```
# org 转换为 Markdown
``` sh
pandoc -f org -t markdown -o output.md input.org
```
