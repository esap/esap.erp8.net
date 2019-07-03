# 数据库驱动
ESAP整合了多种数据库驱动，可以连接大部分数据库。

## SqlServer 2005+
```yaml
driver: mssql
port: 1433
server: localhost
user: sa
pwd: 123
db: esapp1
```

## SqlServer 2000
```yaml
driver: sql2000
port: 1433
server: localhost
user: sa
pwd: 123
db: esapp1
```

## mysql
```yaml
driver: mysql
port: 3306
server: localhost
user: root
pwd: 123
db: db
```

## postgresql
```yaml
driver: postgres
port: 5432
server: localhost
user: postgres
pwd: 123
db: db
```

## sqlite（已停用）
```yaml
driver: sqlite
db: "d:\\mydb.db"
```

## access（已停用）
```yaml
driver: access
db: "d:\\mydb.mdb"
```

## excel（已停用）
```yaml
driver: excel
db: "d:\\mydb.xls"
```

## 驱动企业ERP平台
ESAP服务器直接与SQL交互，使用SQL的程序或系统都可以移植，包括并不限于下列项目：

+ 聚表 JU
+ 慧表 NX
+ 勤哲 ES
+ 活字格 HZG
+ 冠日
+ 金蝶
+ 用友
+ 速达
+ SAP
+ FineReport
+ 快表
+ 云表

## 驱动Excel服务器

* 通常导入或自建`ESAP_xx`模板，保证映射到的`esap_xx`表名和字段名一致。

## 驱动其他系统

* 只要是使用`SQL`，都可以自行建立这些`esap_`前缀的数据表，并保证`名称类型`一致即可。
