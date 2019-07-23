+++
title = "CSS  语法记录"
author = ["Dylan Yang"]
date = 2016-01-06T14:45:00+08:00
tags = ["CSS"]
categories = ["前端"]
draft = false
+++

CSS 是前端开发的基础。CSS 規則由兩個主要的部分構成:選擇器，以及一條或者多條聲明。

```nil

```

\#+BEGIN\_SRC CSS
selector { declaration1; declaration2; ... declarationN;}
\#+END+SRC

選擇器通常是需要改樣式的 HTML 元素。

每條聲明由一個屬性和一個值組成。

屬性是希望設置的樣式/屬性.每個屬性有一個值.屬性和值被冒號分開。

\#+BEGIN\_SRC CSS
selector {property: value}
\#+END+SRC

下面這行代碼的作用是將 h1 元素內的文字顏色定義爲紅色,同時將字體大小設置爲 14 像素。在這個例子中, h1 是選擇器， **color** 和 **font-size** 是屬性, red 和 14px 是值。

\#+BEGIN\_SRC CSS
h1 {color : red; font-size: 14px;}
\#+END+SRC

如果值是若干個詞組,可以選擇給值加引號。

\#+BEGIN\_SRC CSS
p { font-family: "sans serif";}
\#+END+SRC

如果要定義不止一個聲明,則需要用分號將每個聲明分開。

下面的例子展示出如何定義一個紅色文字的居中段落。

最後一條規則是不需要加分號的, 但是最好在每個屬性後都加一個分號。

這樣可以減少修改出錯的可能性。

\#+BEGIN\_SRC CSS
p {
  text-align: center;
  color: black;
  font-family: arial;
}
\#+END+SRC

子元素總是會繼承父元素的屬性。

\#+BEGIN\_SRC CSS
body {
     font-family: Vrdana, sans-serif;
}
\#+END+SRC

子元素會繼承最高級元素的屬性, 即 p, td, ul, ol, li, dl, dt, dd 等都會繼承 body 的屬性. 同樣也可以對子元素進行重寫。

\#+BEGIN\_SRC CSS
body { font-family: Vrdana;}
p { font-family: Times;}
\#+END+SRC

選擇器,派生選擇器: 通過依據元素位置的上下文關係來定義樣式。

\#+BEGIN\_SRC CSS
li strong {
    font-style: italic;
    font-weight: normal;
}
\#+END+SRC

ID 選擇器: 可以爲標有特定 ID 的元素指定樣式。

\#+BEGIN\_SRC CSS
\#red { color: red;}
\#+END+SRC

ID 選擇器可以和派生選擇器一起使用。

\#+BEGIN\_SRC CSS
\#sidebar p{
    font-style: italic;
    text-align: right;
    margin-top: 0.5em;
}
\#+END+SRC

單獨選擇器: 可以單獨發揮作用。

\#+BEGIN\_SRC CSS
\#sidebar {
    border: 1px dotted #000;
    padding: 10px;
}
\#+END+SRC

類選擇器: 以一個點號顯示:

\#+BEGIN\_SRC CSS
.center { text-align: center;}
\#+END+SRC

也可以用作派生選擇器:

\#+BEGIN\_SRC CSS
.fancy td {
    color: #f60;
    background: #666;
}
\#+END+SRC

元素也可以基於它們的類而被選擇:

\#+BEGIN\_SRC CSS
td.fancy {
    color: #f60;
    background: #666;
}
\#+END+SRC

上面的兩個例子中,第一個是類名爲 fancy 的元素內部的屬性設置. 下面的這個是 `<td class`"fancy">= 的元素的屬性設置.

| 選擇器                 | 描述                         |
|---------------------|----------------------------|
| [attribut]             | 用於選取帶有指定屬性的元素   |
| [attribut=value]       | 用於選取帶有指定屬性和值的元素 |
| [attribut~=value]      | 用於選取屬性值中包含指定詞彙的元素 |
| [attribut&vert;=value] | 用於選取帶有以指定開頭的屬性值的元素,該值必須是整個單詞 |
| [attribut^=value]      | 匹配屬性值以指定值開頭的每個元素 |
| [attribut$=value]      | 匹配屬性值以指定值結尾的每個元素 |
| [attribut\*=value]     | 匹配屬性值中包含指定值的每個元素 |

css 允許應用純色作爲背景,也允許使用背景圖片創建相當繁雜的效果。

可以使用 **background-color** 爲元素設置背景色,這個屬性接受任何合法的顏色值。

可以利用這個,把元素的背景配置爲灰色。

\#+BEGIN\_SRC CSS
p { background-color: gray;}

p { background-color: gray; padding:20px;}
\#+END+SRC

**background-color** 是不能繼承的。
