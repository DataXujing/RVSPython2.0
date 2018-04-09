## 机器学习

<font face="Georgia">

对于统计学习，机器学习算法层面，并不陌生，主要来看R与Python的实现机制

### 1 一般流程

数据处理，特征工程，机器学习模型构建，参数调优，模型选择，模型可视化，（模型测试，数据产品开发，模型线上化部署）

---------------
### 2.R中的机器学习实现样例

<font face="Georgia">

+ rattle,caret,mlr,e1071(Bayes,SVM)，rpart,KlaR,kernlab,class,C50,neuralnet,
ipred,randomForest,arules,cluster,fpc,mclust,MASS,kknn,RWeka,sampling,adabag,
nnet,xgboost,lightgbm，etc.

+ R中主流的两套机器学习系统：rattle,caret,mlr,我们可能比较熟悉caret，Rattle底层也是调用caret只不过是有个GUI界面，适用于初学者(trainControl,expand.grid,train,predict),mlr是不同于caret的机器学习系统,mlr包对待各种学习算法和模型实现，有个基本的思路即：Create a Task,Make a learner,Train then.

+ reshape2,plyr,dpylr,tidyr,tidyverse,purrr,sqldf, etc.

+ ggplot2生态系统，lattice,rCharts,Rboken,recharts,ECharts2Shiny，CanvasXpress, etc.（htmlwidgets)

+ 线上化部署：代码对接，R包开发，H2O，pumber包，r2pmml包，opencpu,etc.

---------------------------

### 3.Python中的机器学习实现样例

+ statsmodels,scikit-learn,Pylearn2,Shogun,PyBrain,imbalanced-learn,xgboost,lightgbm, etc.

+ 常用的：statsmodel,sklearn

+ scipy,numpy,pandas,pandasql, etc.

+ matplotlib,bokeh,pyechart,seaborn,ggplot,plotly,etc.

+ 线上化部署: 相对来说独立一些，可以做全套接口或系统。

</font>


### 4.差异与联系


+ Python是一种通用的编程语言，R更偏向于统计分析
+ R有更丰富的统计分析函数，机器学习模型，python长于机器学习
+ R有更好的可视化包，Python正在进步
+ Python与R的核心语法机都比较简单，语法上R更复杂一些

```Python
Python

import statsmodels as sm
result = sm.OLS(y,X).fit
```

```R
R
result <- lm(y~x1+x2+x3,data = A)
```

R是函数到函数，Python是方法到方法


### 5.应用场景

+ 算法研究R,生产实践Python


</font>

