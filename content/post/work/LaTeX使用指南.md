---
title: LaTeX使用指南
date: 2022-12-14
lastmod: 2022-12-23
---
自从用了latex之后，夜夜笙歌，乐不思蜀，再也不想看word一眼。我终于可以告别莫名奇妙的自动编号，不知道哪里冒出来的横线竖线和牵一发而动全身的图片，而去清晰明了，一切尽在掌控的世界生活了。下面是latex使用过程中我总结出的一些经验。内容主要参考[CTAN: Comprehensive TeX Archive Network](https://ctan.org/)，尤其是其中的[lshort-zh-cn.pdf - 清华大学云盘 (tsinghua.edu.cn)](https://cloud.tsinghua.edu.cn/lib/89e56068-5b35-402c-949b-bc9acfc87cbd/file/lshort-zh-cn.pdf)。所有操作都是在[Overleaf, Online LaTeX Editor](https://www.overleaf.com/)中用XeLaTeX完成的。

## latex表格与矩阵

表格和矩阵格式排布逻辑相似，用&表示分列，\\\表示分行。例如矩阵  
$$
\begin{pmatrix}
1  &  2  & 3\\
4  &  5  & 6\\
7  &  8  & 9\\
10 &  11 & 12
\end{pmatrix}\\
$$
可以在amsmath,amssymb,amsfonts宏包下用如下代码写出  
```
\begin{pmatrix}
1  &  2  & 3\\
4  &  5  & 6\\
7  &  8  & 9\\
10 &  11 & 12\\
\end{pmatrix}
```
其中``pmatrix``代表以圆括号表示的矩阵。

## latex图片

latex中插入图片常用graphicx宏包，有两种常见插入方式
```latex
\begin{figure}[htbp]
\centering
\includegraphics[scale=0.2]{filename}
\caption{figure title}
\label{figure}
\end{figure}
```
其中htbp为图片的自动排版方式，分别表示here, top, bottom和浮动状态（忘了p代表哪个单词）。其实一行``\includegraphic[scale = 0.5]{filename}``就完成了插入图片，剩下的不过是在排版、格式上做调整。``scale``处还可以增加其他参数，如``width``, ``height``，``angle``等。

其中使用``minipage ``可并排插入图片，如两张图片并排代码如下：

```latex
\begin{figure}[htbp]
    \begin{minipage}[t]{0.5\linewidth}
        \centering
        \includegraphics[width=\textwidth]{Fig3a.png}
        \centerline{(a) AA}
    \end{minipage}%
    \begin{minipage}[t]{0.5\linewidth}
        \centering
        \includegraphics[width=\textwidth]{Fig3b.png}
        \centerline{(b) BB}
    \end{minipage}
    \caption{AABB}
\end{figure}
```

注意如果行尾不是以``%``结束的话， LATEX 会自动在两行之间加进一个字符的水平间距。所以如果希望得到无缝衔接的图片，记得加百分号。如果希望四张图片以四格漫画般的方式排列，只需要在``\begin{figure}``和``\end{figure}``里再加``minipage``就可以，如果不套``begin``和``end``，则要手动``\\``提示换行位置。[PyMOL作业 - Online LaTeX Editor Overleaf](https://www.overleaf.com/project/63a3176c834b1fae0d8b81c5)可以作为示例。

## 文字样式

LaTeX中常用于调整文字样式的命令如下

|命令|书写方式|文字样式|
|---|---|---|
| \rmfamily | \textrm{…} | roman 衬线字体（罗马体） |
| \sffamily | \textsf{…} | sans serif 无衬线字体 |
|\ttfamily| \texttt{…}| typewriter 等宽字体 |
|\mdseries |\textmd{…} |medium 正常粗细（中等）|
|\bfseries |\textbf{…} |bold face 粗体| 
|\upshape |\textup{…} |upright 直立体 |
|\itshape |\textit{…} |italic 意大利斜体 |
|\slshape |\textsl{…} |slanted 倾斜体 |
|\scshape |\textsc{…}| SMALL CAPS 小型大写字母 |
|\em| \emph{…} |emphasized 强调，默认斜体 |
|\normalfont| \textnormal{…} |normal font 默认字体|
