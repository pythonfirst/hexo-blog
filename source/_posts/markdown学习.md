---
title: markdown学习
date: 2019-12-22 21:54:59
tags: markdown
---


##### Markdown概述
###### 宗旨
Markdown 的目标是实现「易读易写」。

可读性，无论如何，都是最重要的。一份使用 Markdown 格式撰写的文件应该可以直接以纯文本发布，并且看起来不会像是由许多标签或是格式指令所构成。Markdown 语法受到一些既有 text-to-HTML 格式的影响，包括 Setext、atx、Textile、reStructuredText、Grutatext 和 EtText，而最大灵感来源其实是纯文本电子邮件的格式。

###### 兼容 HTML
Markdown 语法的目标是：成为一种适用于网络的书写语言。

Markdown 不是想要取代 HTML，甚至也没有要和它相近，它的语法种类很少，只对应 HTML 标记的一小部分。Markdown 的构想不是要使得 HTML 文档更容易书写。在我看来， HTML 已经很容易写了。Markdown 的理念是，能让文档更容易读、写和随意改。HTML 是一种发布的格式，Markdown 是一种书写的格式。就这样，Markdown 的格式语法只涵盖纯文本可以涵盖的范围。

不在 Markdown 涵盖范围之内的标签，都可以直接在文档里面用 HTML 撰写。不需要额外标注这是 HTML 或是 Markdown；只要直接加标签就可以了。<br>

要制约的只有一些 HTML 区块元素――比如 `<div>、<table>、<pre>、<p>` 等标签，必须在前后加上空行与其它内容区隔开，还要求它们的开始标签与结尾标签不能用制表符或空格来缩进。Markdown 的生成器有足够智能，不会在 HTML 区块标签外加上不必要的 `<p>` 标签。

<pre>
这是一个普通段落。

&lt;table&gt;
    &lt;tr&gt;
        &lt;td&gt;Foo&lt;/td&gt;
    &lt;/tr&gt;
&lt;/table&gt;

这是另一个段落。
</pre>

请注意，在 HTML 区块标签间的 Markdown 格式语法将不会被处理。比如，你在 HTML 区块内使用 Markdown 样式的*强调*会没有效果。
    
HTML 的区段（行内）标签如 `<span>, <cite>和<del>` 可以在 Markdown 的段落、列表或是标题里随意使用。依照个人习惯，甚至可以不用 Markdown 格式，而直接采用 HTML 标签来格式化。举例说明：如果比较喜欢 HTML 的 `<a>` 或 `<img>` 标签，可以直接使用这些标签，而不用 Markdown 提供的链接或是图像标签语法。

和处在 HTML 区块标签间不同，Markdown 语法在 HTML 区段标签间是有效的。
###### 特殊字符自动转换
在 HTML 文件中，有两个字符需要特殊处理： < 和 & 。 < 符号用于起始标签，& 符号则用于标记 HTML 实体，如果你只是想要显示这些字符的原型，你必须要使用实体的形式，像是 `&lt;` 和 `&amp;`。<br>
& 字符尤其让网络文档编写者受折磨，如果你要打「AT&T」 ，你必须要写成「AT&amp;T」。而网址中的 & 字符也要转换。比如你要链接到：

<pre>
http://images.google.com/images?num=30&q=larry+bird
</pre>

你必须要把网址转换写为：

<pre>
http://images.google.com/images?num=30&q=larry+bird
</pre>

才能放到链接标签的 href 属性里。不用说也知道这很容易忽略，这也可能是 HTML 标准检验所检查到的错误中，数量最多的。

Markdown 让你可以自然地书写字符，需要转换的由它来处理好了。如果你使用的 & 字符是 HTML 字符实体的一部分，它会保留原状，否则它会被转换成 &amp;。

所以你如果要在文档中插入一个版权符号©，你可以这样写：

<pre>
&amp;copy;
</pre>

Markdown 会保留它不动。而若你写：

<pre>
AT&amp;T
</pre>

类似的状况也会发生在 < 符号上，因为 Markdown 允许 兼容 HTML ，如果你是把 < 符号作为 HTML 标签的定界符使用，那 Markdown 也不会对它做任何转换，但是如果你写：

<pre>
4&lt;5
</pre>

Markdown 将会把它转换为：

<pre>
4 &amp;lt; 5
</pre>

不过需要注意的是，code 范围内，不论是行内还是区块， < 和 & 两个符号都一定会被转换成 HTML 实体，这项特性让你可以很容易地用 Markdown 写 HTML code （和 HTML 相对而言， HTML 语法中，你要把所有的 < 和 & 都转换为 HTML 实体，才能在 HTML 文件里面写出 HTML code。）

##### 区块元素
###### 段落和换行
一个 Markdown 段落是由一个或多个连续的文本行组成，它的前后要有一个以上的空行（空行的定义是显示上看起来像是空的，便会被视为空行。比方说，若某一行只包含空格和制表符，则该行也会被视为空行）。普通段落不该用空格或制表符来缩进。

「由一个或多个连续的文本行组成」这句话其实暗示了 Markdown 允许段落内的强迫换行（插入换行符），这个特性和其他大部分的 text-to-HTML 格式不一样（包括 Movable Type 的「Convert Line Breaks」选项），其它的格式会把每个换行符都转成 `<br />` 标签。

如果你确实想要依赖 Markdown 来插入 `<br />` 标签的话，在插入处先按入两个以上的空格然后回车。

的确，需要多费点事（多加空格）来产生 `<br />` ，但是简单地「每个换行都转换为 `<br />」`的方法在 Markdown 中并不适合， Markdown 中 email 式的 区块引用 和多段落的 列表 在使用换行来排版的时候，不但更好用，还更方便阅读。
###### 标题
Markdown 支持两种标题的语法，类 Setext 和类 atx 形式。

类 Setext 形式是用底线的形式，利用 = （最高阶标题）和 - （第二阶标题），例如：

<pre>
This is an H1
=============
This is an H2
--------------
</pre>

任何数量的 = 和 - 都可以有效果。

类 Atx 形式则是在行首插入 1 到 6 个 # ，对应到标题 1 到 6 阶，例如：

<pre>
# 这是H1

## 这是H2

###### 这是 H6
</pre>

可以选择性地「闭合」类 atx 样式的标题，这纯粹只是美观用的，若是觉得这样看起来比较舒适，就可以在行尾加上 #，而行尾的 # 数量也不用和开头一样（行首的井字符数量决定标题的阶数）：

<pre>
# 这是H1 #

## 这是H2 ##

###### 这是 H6  ######
</pre>

##### 区块引用Blockquotes
Markdown 标记区块引用是使用类似 email 中用 > 的引用方式。如果你还熟悉在 email 信件中的引言部分，你就知道怎么在 Markdown 文件中建立一个区块引用，那会看起来像是你自己先断好行，然后在每行的最前面加上 > ：

<pre>
> This is a blockquote with two paragraphs. Lorem ipsum dolor sit amet,
> consectetuer adipiscing elit. Aliquam hendrerit mi posuere lectus.
> Vestibulum enim wisi, viverra nec, fringilla in, laoreet vitae, risus.
> 
> Donec sit amet nisl. Aliquam semper ipsum sit amet velit. Suspendisse
> id sem consectetuer libero luctus adipiscing.
</pre>

区块引用可以嵌套（例如：引用内的引用），只要根据层次加上不同数量的 > ：

<pre>
>
> This is the first level of quoting.
> > This id nested blockquote.
>
> Back to the first level.
</pre>

引用的区块内也可以使用其他的 Markdown 语法，包括标题、列表、代码区块等：

<pre>
> ## 这是一个标题。
> 
> 1.   这是第一行列表项。
> 2.   这是第二行列表项。
> 
> 给出一些例子代码：
> 
>     return shell_exec("echo $input | $markdown_script");
</pre>

任何像样的文本编辑器都能轻松地建立 email 型的引用。例如在 BBEdit 中，你可以选取文字后然后从选单中选择增加引用阶层。


###### 列表
Markdown 支持有序列表和无序列表。<br>
无序列表使用星号、加号或是减号作为列表标记：<br>

<pre>
*   Red
*   Green
*   Blue
</pre>

等同于：

<pre>
+   Red
+   Green
+   Blue
</pre>

也等同于：

<pre>
-   Red
-   Green
-   Blue
</pre>

有序列表则使用数字接着一个英文句点：

<pre>
1.   Red
2.   Green
3.   Blue
</pre>

很重要的一点是，你在列表标记上使用的数字并不会影响输出的 HTML 结果，上面的列表所产生的 HTML 标记为：

<pre>
&lt;ol&gt;
&lt;li&gt;Bird&lt;/li&gt;
&lt;li&gt;McHale&lt;/li&gt;
&lt;li&gt;Parish&lt;/li&gt;
&lt;/ol>
</pre>

如果你的标记写成：

<pre>
1.  Bird
1.  McHale
1.  Parish
</pre>

或甚是：

<pre>
3. Bird
1. McHale
8. Parish
</pre>

你都会得到完全相同的 HTML 输出。重点在于，你可以让 Markdown 文件的列表数字和输出的结果相同，或是你懒一点，你可以完全不用在意数字的正确性。

如果你使用懒惰的写法，建议第一个项目最好还是从 1. 开始，因为 Markdown 未来可能会支持有序列表的 start 属性。

列表项目标记通常是放在最左边，但是其实也可以缩进，最多 3 个空格，项目标记后面则一定要接着至少一个空格或制表符。

要让列表看起来更漂亮，你可以把内容用固定的缩进整理好：

<pre>
*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
    Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
    viverra nec, fringilla in, laoreet vitae, risus.
*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
    Suspendisse id sem consectetuer libero luctus adipiscing.
</pre>

但是如果你懒，那也行：

<pre>
*   Lorem ipsum dolor sit amet, consectetuer adipiscing elit.
Aliquam hendrerit mi posuere lectus. Vestibulum enim wisi,
viverra nec, fringilla in, laoreet vitae, risus.
*   Donec sit amet nisl. Aliquam semper ipsum sit amet velit.
Suspendisse id sem consectetuer libero luctus adipiscing.
</pre>

如果列表项目间用空行分开，在输出 HTML 时 Markdown 就会将项目内容用 <p> 标签包起来，举例来说：

<pre>
*  Bird
*  Magic
</pre>

会被转换为： 

<pre>
&lt;ul&gt;
&lt;li&gt;Bird&lt;/li&gt;
&lt;li&gt;Magic&lt;/li&gt;
&lt;/ul&gt;
</pre>

但是这个： 

<pre>
*   Bird

*   Magic
</pre>

会被转换为：

<pre>
&lt;ul&gt;
&lt;li&gt;&lt;p&gt;Bird&lt;/p&gt;&lt;/li&gt;
&lt;li&gt;&lt;p&gt;Magic&lt;/p&gt;&lt;/li&gt;
&lt;/ul&gt;
</pre>

列表项目可以包含多个段落，每个项目下的段落都必须缩进 4 个空格或是 1 个制表符：

<pre>
1.  This is a list item with two paragraphs. Lorem ipsum dolor
    sit amet, consectetuer adipiscing elit. Aliquam hendrerit
    mi posuere lectus.

    Vestibulum enim wisi, viverra nec, fringilla in, laoreet
    vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
    sit amet velit.

2.  Suspendisse id sem consectetuer libero luctus adipiscing.
</pre>

1.  This is a list item with two paragraphs. Lorem ipsum dolor 
    sit amet, consectetuer adipiscing elit. Aliquam hendrerit
    mi posuere lectus.

    Vestibulum enim wisi, viverra nec, fringilla in, laoreet
    vitae, risus. Donec sit amet nisl. Aliquam semper ipsum
    sit amet velit.

2.  Suspendisse id sem consectetuer libero luctus adipiscing.
</pre>

如果你每行都有缩进，看起来会看好很多，当然，再次地，如果你很懒惰，Markdown 也允许：

<pre>
*   This is a list item with two paragraphs.

    This is the second paragraph in the list item. You're
only required to indent the first line. Lorem ipsum dolor
sit amet, consectetuer adipiscing elit.

*   Another item in the same list.
</pre>

如果要在列表项目内放进引用，那 > 就需要缩进：

<pre>
*   A list item with a blockquote:

    > This is a blockquote
    > inside a list item.
</pre>

如果要放代码区块的话，该区块就需要缩进两次，也就是 8 个空格或是 2 个制表符：

<pre>
*   一列表项包含一个列表区块：

        <代码写在这>
</pre>

当然，项目列表很可能会不小心产生，像是下面这样的写法

<pre>
1986. What a great season.
</pre>

换句话说，也就是在行首出现数字-句点-空白，要避免这样的状况，你可以在句点前面加上反斜杠。

<pre>
1986\. What a great season.
</pre>

###### 代码块
预格式化的代码块用于输出编程语言和标记语言. 不同于普通段落, 代码块中的行会被原样呈现. Markdown 会用 `<pre>` 和  `<code>` 标签包围代码块.

要在 Markdown 中插入代码块, 只需要将每一行都缩进 4 个空格或者 1 个水平制表符. 例如, 下面的输入:<br>

<pre>
This is a normal paragraph:

    This is a code block.
</pre>

Markdown 会生成：

<pre>
&lt;p&gt;This is a normal paragraph:&lt;/p&gt;
&lt;pre&gt;&lt;code&gt;This is a code block.&lt;/code&gt;&lt;/pre&gt;
</pre>

只有一级缩进 -- 4 个空格或者 1 个水平制表符 -- 会从代码块中的每一行中移除. 例如:

<pre>
Here is an example of AppleScript:

    tell application "Foo"
        beep
    end tell
</pre>

会生成：

<pre>
&lt;p&gt;Here is an example of AppleScript:&lt;/p&gt;

&lt;pre&gt;&lt;code&gt;tell application "Foo"
    beep
end tell
&lt;/code&gt;&lt;/pre&gt;
</pre>

代码块自动扩展直到碰到未使用缩进的文本 (或者文章结尾).

在代码块内, 英镑符号 (&) 和尖括号 (< 和 >) 或自动转换为 HTML 字符实体. 这使得用 Markdown 包含 HTML 代码非常容易 -- 只需粘贴并缩进, Markdown 会自动转换字符实体. 例如:

<pre>
&lt;div class="footer"&gt;
    &copy; 2004 Foo Corporation
&lt;/div&gt;
</pre>

会生成：

<pre>
&lt;pre&gt;&lt;code&amp;gt;div class="footer"&amp;gt;
    &amp;amp;copy; 2004 Foo Coporation
&amp;lt;/div&amp;gt;
&lt;/code&gt;&lt;/pre&gt;
</pre>

Markdown 的语法在代码块中是无效的的. 例如, 代码块中的星号只是它的字面量而已. 这使得用 Markdown 来书写 Markdown 自身的语法很容易.

###### 水平线
如果一行中只有三个以上的连字符, 星号, 或者下划线则会在该位置生成一个 `<hr />` 标签. 星号和连字符之间的空格也是允许的. 下面的例子都会生成一条水平线:

---
 <center><b>未完待续...<b><center>

---