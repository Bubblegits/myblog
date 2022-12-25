---
title: R语言笔记
date: 2022-12-20
lastmod: 2022-12-24
draft: true
---

R语言用习惯了之后比起excel手感更顺滑，实现功能也更直接。其中一些使用经验记录如下。学习过程中主要参考了[1 R语言介绍 | R语言教程 (pku.edu.cn)](https://www.math.pku.edu.cn/teachers/lidf/docs/Rbook/html/_Rbook/intro.html)，以Rstudio作为IDE。

## 更新

``install.packages("installr")``后可调用``installr``包来更新R. 

```R
library(installr)
updateR()
```

注意及时更新R，一些扩展包只支持在最新的R版本上运行。

## 数据框

> 统计分析中最常见的原始数据形式是类似于数据库表或Excel数据表的形式。 这样形式的数据在R中叫做数据框(data.frame)。 数据框类似于一个矩阵，有个横行、个纵列， 但各列允许有不同类型：数值型向量、因子、字符型向量、日期时间向量。 同一列的数据类型相同。 在R中数据框是一个特殊的列表， 其每个列表元素都是一个长度相同的向量。 事实上，数据框还允许一个元素是一个矩阵， 但这样会使得某些读入数据框的函数发生错误。

## ggplot作图

> Hadley Wickem的ggplot2包是R的一个作图用的扩展包， 它实现了“图形的语法”， 将一个作图任务分解为若干个子任务， 只要完成各个子任务就可以完成作图。 在作常用的图形时， 只需要两个步骤： 首先将图形所展现的数据输入到`ggplot()`函数中， 然后调用某个`geom_xxx()`函数， 指定图形类型，如散点图、曲线图、盒形图等。

首先用``library(ggplot2)``加载ggplot扩展包。

