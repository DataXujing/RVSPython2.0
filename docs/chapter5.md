##  数据库交互


<font face="Georgia">

### 1.操纵数据库的方式

所有数据库都提供API供外部程序调用，R,Python操作数据库与其他数据库客户端的操作是没有差别的。那么当前比较流行的数据库调用方式有三个：DBI，ODBC和JDBC

**DBI**全称是‘数据库接口’，具体指的是perl语言的数据库接口，他是一套基于perl的数据库链接规范，其他语言也可应通过该规范链接数据库。

**ODBC**的全称是‘开放数据库互联’，是微软提供的一套访问数据库的规范和接口，该接口独立于数据库也独立于不同的语言，因此，不同的数据库要安装相应的ODBC.

**JDBC**的全称是‘Java数据库链接’，功能和ODBC很像，但是基于Java,可以非常方便的跨平台和跨数据库。

我们主要介绍基于DBI的链接方式，ODBC，JDBC是类似的（特别的R使用JDBC也要基于DBI)，主要看一下R,Python链接SQLserver，mysql，mongodb,Oracle

---------

### 2.R操作数据库


+ (1).R连接操作sql server（RODBC)

```r
#安装配置：ODBC
library(RODBC)
#在没有readxl包时，我用RODBC操作Excel

配置ODBC
#Server= 数据库服务器名或IP
#Database=数据库名

conn <- odbcConnect("testsql",uid = "sa",pwd = "yourPassword")

res <- sqlQuery(conn, 'select * from weather')

sqlSave(conn,res,"new_weather",append=FALSE)

odbcClose(conn)
```

odbcConnect  可以打开一个连接，返回一个用于随后数据库访问的控制（handle）。 打印一个连接会给出ODBC连接的一些细节，而调用odbcGetInfo 会给出客户端和服务器的一些细节信息。

在一个连接中的表的细节信息可以通过函数 sqlTables 获得。

函数 sqlSave 会把 R 数据框复制到一个数据库的表中，

函数 sqlFetch 会把一个数据库中的表拷贝到 一个 R 的数据框中

通过sqlQuery进行查询，返回的结果是 R 的数据框。

sqlCopy把一个 查询传给数据库，返回结果在数据库中以表的方式保存。 一种比较好的控制方式是首先调用 odbcQuery， 然后 用 sqlGetResults 取得结果。后者可用于一个循环中 每次获得有限行，就如函数 sqlFetchMore 的功能。

连接可以通过调用函数 close 来关闭。

+ (2).R连接操作mysql(RMysql)

```r
library(RMySQL)

#连接
data<-read.csv('C:/Users/Administrator.USER-20170417DX/Desktop/QDTQ.csv',header=F)
data$V7<-1:nrow(data)
names(data)<-c("time","maxTem","minTem","stat","WD","WDJ","id")
conn <- dbConnect(MySQL(), dbname = "qdtqdata", username="root", password="", host="127.0.0.1", port=3306)

#写
dbListTables(conn)
dbWriteTable(conn, "tqhistory", data,append=T,overwrite=F,row.names=F) #写表apeend追加，overwrite覆盖

#读
dbReadTable(conn,"tqhistory")#中文出现乱码，这是因为字符编码格式不统一的问题
dbSendQuery(conn,'SET NAMES UTF8')
dbSendQuery(conn,'SET NAMES GBK')

dbReadTable(conn,"tqhistory")#没有乱码问题了

#查

dbGetQuery(conn, "SELECT * FROM tqhistory limit 3")
##dbGetQuery(conn, "SELECT TOP3 * FROM tqhistory")

res <- dbSendQuery(conn, "SELECT *FROM tqhistory")
data <- dbFetch(res, n=2) #取前2条数据，n=-1时是获取所有数据
data
data <- dbFetch(res, n=-1) #取余下所有数据
data
dbClearResult(res)

dbDisconnect(conn) #关闭连接

# 删数据
dbRemoveTable(connn, "tqhistory")

```

+ (3).R连接操作mongoDB

R操作MongoDB有好个包，RMongo,mongolite,rmongodb

雷同，不在赘述,关于[MongoDB教程可参考,我的有道云笔记](https://note.youdao.com/share/mobile.html?id=7cc4084ec87253a8534a7401919d76e0&type=notebook&from=singlemessage&isappinstalled=0)

+ (4).R连接操作Oracle

注意这个包的安装

```r
library("ROracle");
载入需要的程辑包：DBI
drv <-dbDriver("Oracle")
connect.string <-"(DESCRIPTION = (ADDRESS = (PROTOCOL = TCP)(HOST = 127.0.0.1)(PORT =1521)) (CONNECT_DATA = (SERVER = DEDICATED) (SERVICE_NAME = orcl)))"
con <- dbConnect(drv,username = "iind_1609", password = "iind_1609", dbname = connect.string)
rs <- dbSendQuery(con,"select * from CFG_DB ")
data<-fetch(rs);
data

```

+ (5).pool

pool包的目标是抽象连接管理的逻辑和从远程数据库获取新连接的性能成本,这些问题在交互环境中尤为突出。像shiny app的应用程序（连接到远程数据库），甚至在R控制台。因此这个包对于shiny的开发者来说最有实用价值，pool实际上是结合了DBI和dplyr,所有内容上来说没有什么新东西。
用起来不会觉得陌生，并且Rstudio提供了详实的说明文档：<http://db.rstudio.com/>,<http://shiny.rstudio.com/articles/#data>

-----------------


### 3.Python操作数据库


+ (1).Python操作sql server(pyodbc)

pyodbc模块是用于odbc数据库（一种数据库通用接口标准）的连接，不仅限于SQL server，还包括Oracle,MySQL,Access,Excel等。
<https://wiki.python.org/moin/SQL%20Server>

```python

conn = pyodbc.connect(r'DRIVER={SQL Server Native Client 11.0};SERVER=192.168.1.1,3433;DATABASE=test;UID=user;PWD=password')

#{SQL Server} - released with SQL Server 2000
#{SQL Native Client} - released with SQL Server 2005 (also known as version 9.0)
#{SQL Server Native Client 10.0} - released with SQL Server 2008
#{SQL Server Native Client 11.0} - released with SQL Server 2012

cursor = conn.cursor()
cursor.execute("select user_id, user_name from users")
rows = cursor.fetchall()
for row in rows:
    print(row.user_id, row.user_name)

#增删改
cursor.execute("insert into products(id, name) values ('pyodbc', 'awesome library')")
conn.commit()
cursor.execute("delete from products where id <> ?", 'pyodbc')
print('Deleted {} inferior products'.format(cursor.rowcount))
conn.commit()

```

> [pyodbc 官方文档](http://mkleehammer.github.io/pyodbc/)
> 
> [pyodbc官方wiki](https://github.com/mkleehammer/pyodbc/wiki)
> 
> [pyodbc的简单使用](http://my.oschina.net/zhengyijie/blog/35587)
> 

+ (2).Python操作mysql


Python2:

pip install MySQL-python

import MySQLdb

Python3:

pip install PyMySQL

import PyMySQL

+ (3).Python操作mongoDB(PyMongo)

现在我们已经描述了MongoDB的是什么，让我们来看看如何在Python中实际使用它。由MongoDB开发者发布的官方驱动程序PyMongo:<https://pypi.python.org/pypi/pymongo/>，这里通过一些例子介绍，但你也应该查看完整的文档:<https://api.mongodb.com/python/current/>


+ (4).Python操作Oracle(cx_Oracle)

<https://oracle.github.io/python-cx_Oracle/>


+ (5).pyqt,django等有独立的数据库操作流程

Python的Gui开发及django等有独立的数据库操作

import PyQt5.QtSql as sql (感觉比PyMySQL快一些）

django 模型


个人观点： 对于数据库的操作两种语言都有提高的空间，解决操作数据库慢，有些还存在多库不可以同时连接的情况。

------

### 4.Reference



[1].<https://github.com/DataXujing/MySQL-R-Python>

</font>