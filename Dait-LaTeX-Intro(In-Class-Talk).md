# LaTeX 简介
如果你编辑过数学物理方面的文档，你应该遇到过这种需求：

* 插入希腊字母和各种数学符号
* 输入分式、根式、求和……

Word 里内置的 MathType 确实可以满足需求，但有不少局限性：

* 大量公式的编辑、复制、迁移等较麻烦
* 公式的居中、编号、引用
* 正版 MathType <u>贵</u>

当然。用 word 排公式也可以很好看，但为什么不试试 LaTeX 呢？
## What is LaTeX?
LaTeX 是一个文档准备系统 (Document Preparing System) 。

非常适用于生成高印刷质量的科技类和数学类文档。它也能够生成所有其他种类的文档，小到简单的信件，大到完整的书籍。

LaTeX 使用 TeX 作为它的排版引擎。
### 介绍：TeX 
TeX 是高德纳 (Donald E. Knuth) 为排版文字和数学公式而开发的软件。

1977 年，正在编写《计算机程序设计艺术》的高德纳意识到每况愈下的排版质量将影响其著作的发行，为扭转这种状况，他着手开发 TeX，发掘当时刚刚用于出版工业的数字印刷设备的潜力。

1982 年，高德纳发布 TeX 排版引擎，而后在 1989 年又为更好地支持 8-bit 字符和多语言排版而予以改进。

TeX 以<u>其卓越的稳定性、跨平台能力和几乎没有 bug </u> 的特性而著称。
### 介绍：LaTeX
LaTeX 由 Dr. Lamport 开发，是一种使用 TeX 程序作为排版引擎的格式 (format)，可以粗略地将它理解成是对 TeX 的一层封装。

LaTeX 最初的设计目标是分离内容与格式，以便作者能够专注于内容创作而非版式设计，并能以此得到高质量排版的作品。
### LaTeX 编译
* 编译器有 `VIM-LaTeX`, `TeXstudio`，线上：`Overleaf`
* 编译命令有 `pdfLaTeX`, `XeLaTeX`, `LuaTeX` 等
* 编译会在 `*.tex` 文件目录下生成 `*.log` `*.bib` `*.idx` 等文件
* 每个宏包和文档类都是带特定扩展名的文件
### LaTeX 命令
* 命令以反斜杠 `\` 开头，大小写敏感
* 命令作用内容用花括号 `{}` 括起，比如 `\texttt{Hello}`
* 环境以 `\begin` 开头和 `\end` 结尾
	```LaTeX
	\begin{<environment name>}
		[<optional arguments>]{<mandatory arguments>}...
	% write something here
	\end{<environment name>}
	```
### LaTeX 文档和宏包
* 文档性质
	```LaTeX
	\documentclass[<options>]{article}
	```
* 宏包：在使用 LaTeX 时，时常需要依赖一些扩展来增强或补充 LaTeX 的功能，比如排版复杂的表格、插入图片、增加颜色甚至超链接等等。这些扩展称为宏包。

	```LaTeX
	\usepackage[<options>]{<package-name>}
	```
## LaTeX 代码示例
### 最基本的需求：写内容、显示公式

比如我们希望显示如下内容

> The Pythagorean theorem is $a^2 + b^2 = c^2$.

在新建 `formula.tex` 文件后，代码如下
```LaTeX
\documentclass{article}
\usepackage{amsmath} % macro pack
\begin{document} % main body
	The Pythagorean theorem is $a^2 + b^2 = c^2$.
\end{document}
```
从上到下即，文档性质 `artical`，使用 `amsmath` 宏包，在 `document` 环境中写下文档内容，将公式用 `$$` 括起来。

因此，在 `document` 环境内的内容才是文档需要显示的内容，在此之前都是起手式，下面的代码将省略起手式。

### 公式居中
利用 `equation` 环境，可以让公式新开一行，将上面的代码改为
```LaTeX
The Pythagorean theorem is:
\begin{equation}
	a^2 + b^2 = c^2.
		\label{pythagorean}
\end{equation}
Equation \eqref{pythagorean} is called `Gougu theorem' in Chinese.
```
编译结果
> The Pythagorean theorem is:
> $$\begin{equation}
	a^2 + b^2 = c^2.
\end{equation}$$
> Equation (1) is called `Gougu theorem' in Chinese.

如果我们不希望有编号，可将环境添加星号，即 `equation*`
```LaTeX
\begin{equation*}
	a^2 + b^2 = c^2.
\end{equation*}
```
若让多行公式按等号对齐，则需要 `align` 环境
```LaTeX
\begin{align}	 % align formulas
a & = b + c \\
  & = d + e
\end{align}
```
编译结果
> $$\begin{align}a & = b + c \\
  & = d + e
\end{align}$$

若不需要编号，在该行末添加 `\notag` 即可。

### 复杂的公式
> $$\lim_{n\to\infty}
	\sum_{k=1}^n
	\frac{1}{k^2}=	% fraction
	\frac{\pi^2}{6}
$$
Directly,
```LaTeX
\[ % write excellent formula here...
	\lim_{n\to\infty}
	\sum_{k=1}^n
	\frac{1}{k^2}=	% fraction
	\frac{\pi^2}{6}
\]
```
或，矩阵
> $$\begin{bmatrix}	% matrix type b
x_{11} & x_{12} & \ldots & x_{1n}\\
x_{21} & x_{22} & \ldots & x_{2n}\\
\vdots & \vdots & \ddots & \vdots\\
x_{n1} & x_{n2} & \ldots & x_{nn}\\
\end{bmatrix}
$$
```LaTeX
\[
	\begin{bmatrix}	% matrix type b
		x_{11} & x_{12} & \ldots & x_{1n}\\
		x_{21} & x_{22} & \ldots & x_{2n}\\
		\vdots & \vdots & \ddots & \vdots\\
		x_{n1} & x_{n2} & \ldots & x_{nn}\\
	\end{bmatrix}
\]
```
### 文档元素

为 LaTeX 文档起一个响亮的标题
```LaTeX
\title{响亮的标题}	% set the title
\author{Dait}		% set the author
\maketitle			% make the title in the document
```
注：中文支持需要 `ctex` 等宏包

LaTeX 文档有七层：
```LaTeX
\chapter{第一章}
	\section{第一节}
		\subsection{第一小节}
			\subsubsection{第一小小节}
				\paragraph{第一段}
					\subparagraph{第一副段}
```
在文档开头使用 `\tableofcontents` 可自动生成目录。
### 自定义命令
```LaTeX
\newcommand[\<name>][<num>]{<definition>}
```
自定义新命令可以极大的提高写代码的效率。

e.g. 微积分中，直接写偏导数 $\frac{\partial f}{\partial x}$ 需要
```LaTeX
\frac{\partial f}{\partial x}
``` 
其实关键部分只在于 `f` 和 `x`，因此可以定义
```LaTeX
\newcommand[\pv][2]{\frac{\partial #1}{\partial #2}}
```
这样写
```LaTeX
\pv fx 
```
就可以了。
## LaTeX vs. MS Office Word?
对比 LaTeX 和 MS Office Word？

TeX 是一个排版引擎，LaTeX 是其封装。
而 Word 是字处理工具。
二者的设计目标不一致，也各自有自己的适用范围。

但如果想得到像右图效果的 .pdf，LaTeX 的实现效率肯定是比 Word 高的。(当然，二者都能实现)

从文字排版来说，LaTeX 的断行和断页采用的是动态规划算法，而 Word 是贪心算法（只管当前行排满）
在一行末尾出现长单词的时候，Word 就会显得版面不均衡。
## LaTeX 的优点
1. 专业的排版输出

	只需专注于一些组织文档结构的基础命令，很少操心文档的版面设计

2. 方便而强大的公式排版
   
   尤其是数学物理公式

3. 完备的排版元素
   
   很容易生成复杂的脚注、交叉引用、参考文献、目录等

4. 强大的可拓展性
   
   跨平台、免费开源、输出稳定数以千计的宏包以拓展 LaTeX 功能

## LaTeX 的不足
1. 入门门槛高

	新手写 Word 还能得到一篇文档，但遇到 LaTeX 可能连编译出文档都得费一段时间。而且 LaTeX 插入表格和图片的功能对新手不太友好。

2. 不容易排查错误
   
   可能仅仅是公式中写了一个中文逗号，编译器就能报上百个错。虽然能够提示错误，但不提供调试机制，有时错误提示还很难理解。

3. 不容易自定义样式
   
   按照既定样式走很顺畅，但是想修改既定样式可能非常困难

4. 不能“所见即所得”，需要不断编译
## 总结
作为一个排版系统，LaTeX 排版公式的能力是相当优秀的。

数学物理类的文档，用 LaTeX 编写具有绝对的优势；
对学生来说。数理系课程的笔记，LaTeX 配上识别公式的 Mathpix 和所见即所得的 AxMath 等软件，可以大大提升效率。作业、实验报告和论文也大有 LaTeX 的用武之地。

总之，还没用过 LaTeX 的同学们，试试 LaTeX 吧！