## '造轮子'

<font face="Georgia">


强烈不建议大家自己'造轮子'！！！


### 1.R
R中造轮子就是写一些开源的包，回馈给开源社区，本人从开始的命令行写R包一直到Rstudio写R包，有20多个，大部分都托管在Github及CRAN。

我个人对写的R包分成了三类：

+ 功能性的R包（[LN0SCIs](https://CRAN.R-project.org/package=LN0SCIs)）

+ 基于gwidgets的R包（[Ricetl](https://CRAN.R-project.org/package=Ricetl))

+ 基于htmlwidgets的R包 ([XuJIngd3plus](https://github.com/DataXujing/XuJIngd3plus))

------

+ CRAN(FTP 上传 + 邮件通知。目前 Kurt Hornik 管理 Linux 包的编译，Uwe Ligges 负责 Windows 包的编译，都是人工管理):CRAN对R包的审核比较严格，有一点不OK都不行

+ Github(GIT):这个包审核要宽松了，基本都可以通过，我好多R包目前都只在Github上（devtools::install_github('DataXujing/pkgname')

+ R-forge(SVN,基本废掉了):我没用过


------

### 2.Python

Python造轮子也是写一些开源的Python模块，包（NB的人写框架，再NB的人开发编程工具）。我个人对写的Python包也分为3类

+ 功能性的Python包([LN0SCIs](https://pypi.python.org/pypi/LN0SCIs/0.1.1),[Icics](https://pypi.python.org/pypi/Icics/0.3.3),[optiation](https://pypi.python.org/pypi/Optiation/0.3.6))

+ 命令行开发(django,mkdocs)

+ 其他（不好意思，我没接触过）

------

+ PyPI（the <font color='red'>Py</font>thon <font color='red'>P</font>ackage <font color='red'>I</font>ndex：LN0SCIs,Icics,optiation (pip insytall pkgname)

+ Github:example  (pip install https://github.com/jkbr/httpie)
 
--------------------

### 3. 

个人经验，请参考：

学会站在巨人的肩膀上，做一个‘调包侠’挺好，

这句话的意思是：不要轻易‘造轮子’，浪费时间，做无用功，只能满足自己的‘装B’心里，别无益处

</font>