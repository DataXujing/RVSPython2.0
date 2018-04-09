## R Python与大数据

<font face="Georgia">

### 1.R

R在诞生初期最容易被人诟病的特点就是运算性能不强。

+ R是单线程的，无法使用多核运算，造成资源浪费
+ R是一种解释性语言，使得R在定义的函数在每次运行之前都会解释一遍，牺牲的程序的性能
+ R默认是内存内运算
+ R的优点在于矩阵运算，但是R的矩阵运算要比一些商业软件更慢。

除了第一条，其他几条并不是R自身的问题。

近年来R的开发团队，包括开源社区的R user都意识到了R的一些不足，不断优化底层代数运算库，也有加强版的R版本，像微软的R server(2017年4月份已经可以免费使用，我对比了一下，速度比RGUI没有差别,Microsoft Machine Learning Server 2017年09月），但是Rserver提供了几套全新的机器学习包，微软关于R server及这些机器学习，数据处理的包的介绍有1千多页，感兴趣可以去看一下，还有就是普度大学的SupR（2016年4月份）,实现了类似于JAVA的多线程和并发行模型，支持多线程，同时R的第三方库也可以做到并行预算，处理大矩阵。

Rhadoop，Sparklyr等包也都比较成熟，bigmemory,foreach,multicore,snow,snowfall,biglm,bigrf,ff,Rmpi,parallel,doParallel


### 2.Python

为Linux系统而生，相比R在这方面要好一些，它有更像面向对象编程的面向对象编程机制，不像R(基础面向对象编程，S3,S4,R5,每个都不太像真正的面向对象），对于hadoop及spark(pySpark)等支持也不在话下，线程进程管理机制比R完善的多。


### 3.结论

我个人并没有参与过具体的使用hadoop,spark完成的项目，对其研究仅停留在理论阶段，个人认为：大数据方面我更看好Python

</font>