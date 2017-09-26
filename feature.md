# 数据库驱动
ESAP整合了多种数据库驱动，可以连接大部分数据库，部分示例配置如下。

* [SqlServer 2005+](#SqlServer 2005+)
* [SqlServer 2000](#SqlServer 2000)
* [mysql](#mysql)
* [postgresql](#postgresql)
* [sqlite](#sqlite)
* [access](#access)
* [excel](#excel)
* [驱动企业平台](#驱动企业平台)

## SqlServer 2005+
```
driver: mssql
port: 1433
server: localhost
user: sa
pwd: 123
db: esapp1
```

## SqlServer 2000
```
driver: sql2000
port: 1433
server: localhost
user: sa
pwd: 123
db: esapp1
```

## mysql
```
driver: mysql
port: 3306
server: localhost
user: root
pwd: 123
db: db
```

## postgresql
```
driver: postgres
port: 5432
server: localhost
user: postgres
pwd: 123
db: db
```

## sqlite
```
driver: sqlite
db: "d:\\mydb.db"
```

## access
```
driver: access
db: "d:\\mydb.mdb"
```

## excel
```
driver: excel
db: "d:\\mydb.xls"
```

## 驱动企业平台
ESAP服务器直接与SQL交互，使用SQL的程序或系统都可以移植，包括并不限于下列项目：

+ 聚表
+ 勤哲
+ 冠日
+ 金蝶
+ 用友
+ 速达
+ SAP
+ FineReport
+ 快表
+ 云表

#### 驱动Excel服务器

* 如果你使用的是9.4+版，恭喜你，只需要将安装包中的`ESAP_提醒`模板导入到你的生产应用中，然后启动esap服务器即可。

* 如果是es9.4以下版本，例如7.1.7，8.4，9.2等，则需要自行建立这些`模板`，并保证表名和字段名一致即可。

#### 驱动其他ERP系统

* 只要是使用SQL，都可以自行建立这些数据表，并保证名称类型一致即可。
