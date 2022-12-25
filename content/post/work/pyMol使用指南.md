---
title: PyMOL使用指南
date: 2022-12-19
draft: true
---
本文内容主要参考[PyMOLWiki](https://pymolwiki.org/index.php/Main_Page)和[入门教程 — PyMOL中文教程 2022.09 文档 (chenzhaoqiang.com)](http://pymol.chenzhaoqiang.com/intro/startManual.html)

## 一个例子

文献 *Crystal structure of yeast hexokinase PI in complex with glucose: A classical ‘‘induced fit’’ example revised* 中有如下一张图

![image-20221221123101736](https://s2.loli.net/2022/12/21/wiQuzZgmRMJ4vaG.png)

该文献所研究的hexokinase在PDB中编号为3B8A，下载蛋白格式文件后可按如下方法操作。

首先分别选择底物和与底物互作的氨基酸。图中底物为葡萄糖，与其互作的氨基酸有Lys176, Asp211, Glu269, Glu302。``select res, (resi 176, resi 211, resi 269, resi 302)``选中，在选中标签中将底物命名为``ligs``, 互作残基命名为``ress``, 通过代码显示底物与互作残基

```
hide #隐藏所有对象
show sticks, ligs | ress #|表示或
```

并添加对应标签，输出结果如图所示。

![image-20221221124526915](C:/Users/bubble/AppData/Roaming/Typora/typora-user-images/image-20221221124526915.png)


PyMOL的命令中，第一个词表示函数，后面的词语都表示变量，不同变量之间要加``,``。注意此时lig是一套选择方式而非一些分子（是selection而非object），这种表示方法可能会给后面的工作增加麻烦。可以通过``create ligs, lig``命令把lig化为分子，同时可以用``remove ligs``来在3b8a中移除底物，避免重复操作。最好不要给selection和object赋相同名称，否则会引起混淆。在wizard -> measurement 中可选择两个原子并在其间添加黄色虚线，效果如图。

![image-20221221130856825](https://s2.loli.net/2022/12/21/9UpAf4ZHnvtu32G.png)

使用``color wheat, lig & name C*``使底物中的碳原子变为麦色。发现标签有遮挡，在右下角把mouse mode改为3-button editing之后先按住ctrl, 再用鼠标左键拖动标签即可调整其位置。

![image-20221221154029923](https://s2.loli.net/2022/12/21/puXrAkQVtc5L9mH.png)

而后可以使用

```PyMOL
show cartoon, 3b8a
set transparency, cartoon, 0.7
bg_color white
```

达到如下效果（下图颜色经过进一步调整）

![hexo active](C:/Users/bubble/Desktop/Pymol%20%E4%BD%9C%E4%B8%9A/hexo%20active.png)

和目标图片相比基本相似。
