# 数据库兼管
ESAP整合了多种数据库驱动，可以连接大部分数据库，部分示例配置如下。

* [SqlServer 2005+](#SqlServer 2005+)
* [SqlServer 2000](#SqlServer 2000)
* [mysql](#mysql)
* [postgresql](#postgresql)
* [access](#access)
* [excel](#excel)
* [兼管其他平台](#兼管其他平台)

## SqlServer 2005+
```
dbdriver: mssql
dbport: 1433
server: localhost
userid: sa
pwd: 123
dbname: esapp1
```

## SqlServer 2000
```
dbdriver: sql2000
dbport: 1433
server: localhost
userid: sa
pwd: 123
dbname: esapp1
```

## mysql
```
dbdriver: mysql
dbport: 3308
server: localhost
userid: root
pwd: 123
dbname: dbName
```

## postgresql
```
dbdriver: postgres
dbport: 5432
server: localhost
userid: postgres
pwd: 123
dbname: dbName
```

## access
```
dbdriver: access
dbname: "d:\\mydb.mdb"
```

## excel
```
dbdriver: excel
dbname: "d:\\mydb.xls"
```

## 兼管其他平台
ESAP服务器直接与SQL交互，使用SQL的程序或系统都可以移植，包括并不限于下列项目：

+ 勤哲Excel服务器
+ 冠日网络Excel平台
+ 金蝶
+ 用友
+ 速达
+ SAP
+ FineReport
+ 快表
+ 云表

#### 兼管Excel服务器

* 如果你使用的是9.4+版，恭喜你，只需要将压缩包中的`微信提醒`模板导入到你的生产应用中，然后启动esap服务器即可。

* 如果是es9.4以下版本，例如7.1.7，8.4，9.2等，则需要自行建立这些`模板`，并保证表名和字段名一致即可。

#### 兼管其他平台或ERP系统

* 只要是使用SQL，都可以自行建立这些`模板`的数据表，并保证名称类型一致即可。
