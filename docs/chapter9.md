## R与Python的相互调用


<font face="Georgia">

R与Python都号称‘胶水语言’，他们和Java,C,C++,C#都有可以很好的相互调用，以至于他们的一些包都是由这些语言开发的。这也使得数据分析师，算法工程师可以很好的将自己训练好的算法做线上化部署及数据产品的集成开发。

R与Python当然也可以相互调用!!!

------

### 1.R调用Python

+ rpython：不怎么好用（之前的一个项目：shiny调python算法，最终成功了，但是花了不少时间解决一些数据交互的问题，代码在<https://github.com/DataXujing/IRSModel_py_shiny>）

+ R Markdown原生支持多语言块（但是代码块之间不能正常通信，并且对Python的图形渲染不OK)

+ reticulate:Rstudio操刀的产品，不错，我已把官方文档翻译成中文教程，在我的个人主页上<http://dataxujing.coding.me/>


------

### 2.Python调用R

+ rpy2:也是不错的，但不能很好支持pyinstaller，前期尝试过可执行文件的生成，出了点小问题

+ jupyter notebook的魔法函数

-------------

### 4.Python和R之间的双向翻译器

PolYamoR是第一个能达到全透明，不矛盾、并且管理复杂编程的多语言编程系统。PolYamoR可以使纯Python代码翻译成纯R代码，反之亦然

------

### 3.学习文档

[1].<https://github.com/DataXujing/PythonVsR>

[2].<http://dataxujing.coding.me/>翻译的reticulate包

[3].[PolYamoR的简介](https://mp.weixin.qq.com/s/rgvgPdYwVkRx6JKzO6Me_g)

[4].<https://github.com/dataiku/PolYamoR>

</font>
