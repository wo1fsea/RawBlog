title: 生存技能 01. Markdown & LaTex Formulas
date: 2016-11-27 00:21:11
tags: [Survival Skill, Markdown, LaTex]

---

做笔记写文档最恼人的，可能就是文档标题格式字体字号等等的设置了。所幸用 Markdown 之后，都不用怎么考虑这些细节问题。然而，偶然读书遇到公式，想要记录下来还是挺麻烦的。最好的方法可能是截图，但是还是有格式不一致，不能二次编辑等等问题。这两天发现 atom 的 MPP 插件居然支持 LaTex 的公式编辑和渲染，再配合 google api 的 LaTex 公式渲染，正好解决了这个困扰已久的问题。

恰好最近正在反思，自己平时看书翻资料时间花不少，但记录总结的却不多。正好借机培养下习惯，从一些基础的东西开始整理。掌握这些工具，怎么看都是生存技能，所以这篇叫《生存技能 01. Markdown & LaTex Formulas》，从用 Markdown 和 LaTex 开始。

 <!-- more -->

 ## Markdown

> Markdown 是一种轻量级标记语言，创始人为约翰·格鲁伯（John Gruber）。它允许人们“使用易读易写的纯文本格式编写文档，然后转换成有效的XHTML(或者HTML)文档”。[4]这种语言吸收了很多在电子邮件中已有的纯文本标记的特性。 -- wikipedia

更具体的介绍可见 [Markdown官方主页](http://daringfireball.net/projects/markdown/) 。

下面列出 Markdown 语法的基本元素。

### 标题

Markdown 标题可以选用下列两种风格：

风格1:

    标题一
    ===

    标题二
    ---

或者，风格2，由1到6个#开头的标题形式：

    # 标题一

    ## 标题二

    ###### 标题六

### 引用

Markdown 引用使用 > 符号作为行起始字符，如下：

    > 引用

多行引用可写作：

    > 引用行1
    引用行2

或：

    > 引用行1
    > 引用行2

### 列表

无序列表写作：

    * a
    * b
    * c

或：

    + a
    + b
    + c

或：

    - a
    - b
    - c

有序列表：

    1. a
    2. b
    3. c

或：

    1. a
    1. b
    1. c

### 表格

在 Markdown 中使用如下格式：

    |h1  |h2  |h3  |
    |:---|:--:|---:|
    |v1  |v2  |v3  |

将生成下列表格：

|h1  |h2  |h3  |
|:---|:--:|---:|
|v1  |v2  |v3  |


### 代码块

Markdown 中缩进一个字表符或者4个空格表示一个代码块：

    这是文章。
        这是代码块。

或者使用

### 分割线

单行使用三个以上的下划线，星号，减号可以生成一个分割线。

    * * *

    ***

    *****

    - - -

    ---------------------------------------

### 图片

使用下列方式可插入图片：

    ![图片描述](图片地址)

### 链接

使用下列方式可插入链接：

    [链接描述](链接地址)

### 强调

在 Markdown 中，使用 `*斜体*` 表示 *斜体*，使用 `**粗体**` 表示 **粗体** 。


## LaTex 公式

### 上下标

在 LaTex 中，使用 ^ 表示上标， _ 表示下标。

例如：

    \[ E=mc^2 \]

表示

![](http://chart.googleapis.com/chart?cht=tx&chl=E=mc^2)


### 根式与分式

根式用\sqrt{·}来表示，分式用\frac{·}{·}来表示（第一个参数为分子，第二个为分母）。

例如：

    \[ \Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a} \]

表示：

![](http://chart.googleapis.com/chart?cht=tx&chl=\Large x=\frac{-b\pm\sqrt{b^2-4ac}}{2a})

\documentclass{article}
%
% 数学环境支持
% %%%%%%%%%%%%%%%%%%%%%%%%%%%%%%
\usepackage{amsmath}
\begin{document}
$\sqrt{x}$, $\frac{1}{2}$.

\[ \sqrt{x}, \]

\[ \frac{1}{2}. \]
\end{document}
可以发现，在行间公式和行内公式中，分式的输出效果是有差异的。如果要强制行内模式的分式显示为行间模式的大小，可以使用\dfrac, 反之可以使用\tfrac。

运算符

一些小的运算符，可以在数学模式下直接输入；另一些需要用控制序列生成，如

\[ \pm\; \times \; \div\; \cdot\; \cap\; \cup\; \geq\; \leq\; \neq\; \approx \; \equiv \]
\[ \sum, \prod, \lim, \int \]

连加、连乘、极限、积分等大型运算符分别用生成。他们的上下标在行内公式中被压缩，以适应行高。我们可以用\limits和\nolimits来强制显式地指定是否压缩这些上下标。例如：

$ \sum_{i=1}^n i\quad \prod_{i=1}^n $
$ \sum\limits _{i=1}^n i\quad \prod\limits _{i=1}^n $
\[ \lim_{x\to0}x^2 \quad \int_a^b x^2 dx \]
\[ \lim\nolimits _{x\to0}x^2\quad \int\nolimits_a^b x^2 dx \]
多重积分可以使用\iint, \iiint, \iiiint, \idotsint 等命令输入。

\[ \iint\quad \iiint\quad \iiiint\quad \idotsint \]
分隔符

各种括号用(), [], \{\}, \langle\rangle 等命令表示；注意花括号通常用来输入命令和环境的参数，所以在数学公式中它们前面要加\。因为 LaTeX 中|和\|的应用过于随意，amsmath 宏包推荐用\lvert\rvert和\lVert\rVert取而代之。

为了调整这些分隔符的大小，amsmath宏包推荐使用\big, \Big, \bigg, \Bigg放在上述括号前面调整大小。

\[ \Bigg(\bigg(\Big(\big((x)\big)\Big)\bigg)\Bigg) \]
\[ \Bigg[\bigg[\Big[\big[[x]\big]\Big]\bigg]\Bigg] \]
\[ \Bigg \{\bigg \{\Big \{\big \{\{x\}\big \}\Big \}\bigg \}\Bigg\} \]
\[ \Bigg\langle\bigg\langle\Big\langle\big\langle\langle x
\rangle\big\rangle\Big\rangle\bigg\rangle\Bigg\rangle \]
\[ \Bigg\lvert\bigg\lvert\Big\lvert\big\lvert\lvert x
\rvert\big\rvert\Big\rvert\bigg\rvert\Bigg\rvert \]
\[ \Bigg\lVert\bigg\lVert\Big\lVert\big\lVert\lVert x
\rVert\big\rVert\Big\rVert\bigg\rVert\Bigg\rVert \]
省略号

省略号用\dots, \cdots, \vdots, \ddots 等命令表示。\dots 和\cdots的纵向位置不同，前者一般用于有下标的序列。

\[ x_1,x_2,\dots ,x_n\quad 1,2,\cdots ,n\quad
\vdots\quad \ddots \]
矩阵

amsmath 的pmatrix, bmatrix, Bmatrix, vmatrix, Vmatrix 等环境可以在矩阵两边加上各种分隔符。

\[ \begin{pmatrix} a&b\\c&d \end{pmatrix} \quad
\begin{bmatrix} a&b\\c&d \end{bmatrix} \quad
\begin{Bmatrix} a&b\\c&d \end{Bmatrix} \quad
\begin{vmatrix} a&b\\c&d \end{vmatrix} \quad
\begin{Vmatrix} a&b\\c&d \end{Vmatrix} \]
效果图：

使用smallmatrix环境，可以生成行内公式的小矩阵。

Marry has a little matrix $ ( \begin{smallmatrix} a&b\\c&d \end{smallmatrix} ) $.
效果图：

多行公式

有的公式特别长，我们需要手动为他们换行；有几个公式是一组，我们需要将他们放在一起；还有些类似分段函数，我们需要给它加上一个左边的花括号。

长公式

不对齐

无须对齐的长公式可以使用multline环境。

\begin{multline}
x = a+b+c+{} \\
d+e+f+g
\end{multline}
效果：

如果不需要编号，可以使用multline*环境代替。

分段函数

分段函数可以用cases次环境来实现，它必须包含在数学环境之内。

\[ y=\ begin{cases}
-x,\quad x\leq 0 \\
x,\quad x>0
\end{cases} \]


\[a\]

\[\frac{1}{2}.\]
