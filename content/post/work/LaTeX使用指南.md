---
title: LaTeX使用指南
date: 2022-12-14
lastmod: 2022-12-15
---
自从用了latex之后，夜夜笙歌，乐不思蜀，再也不想看word一眼。我终于可以告别莫名奇妙的自动编号，不知道哪里冒出来的横线竖线和牵一发而动全身的图片，而去清晰明了，一切尽在掌控的世界生活了。下面是latex使用过程中我总结出的一些经验。

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
其中htbp为图片的自动排版方式，分别表示here, top, bottom和浮动状态（忘了p代表哪个单词）。对排版和图注要求不高的话也可以一行``\includegraphic[scale = 0.5]{filename}``搞定。



