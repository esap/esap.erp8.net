# SQL模板

* 从2.7版开始，ESAP引入了[sqlt库](https://github.com/it512/sqlt)作为sql操作的中间件。

* 同时，村长在ESAP内部实现了许多自定义函数，使用sql模板，你可以快速打造基于SQL的数据API。

## 什么是API

* API是前后端分离后的一种后端服务，专注于提供数据访问，ESAP的API服务采用流行的json格式。

* ESAP启动时，会自动建立`/api/*`,`/api2/*`,`/es/*`,`/es2/*`等几组API路由，APP和Admin等扩展功能就是使用这些api,实现数据查询和创建ES表单等功能。

## 查询服务

* 我们以APP的库存查询为例演示sql模板的查询输出功能。

* 在APP的库存查询搜索框输入`手机`时，前端(APP)就会向后端(ESAP)发起一个GET请求，请求地址是`/api2/vlbq?s=手机`,然后ESAP返回数据，APP展示数据。

![](./img/sqlt1.png)

* ESAP是如何获取SQL数据的呢？实际上，根据请求参数执行了`sql/api2/*.get`中的`vlbq`模板，然后返回sql查询结果，下面是模板定义。
```sql
{{define "vlbq"}}	
	select * from vlbq where 名 like '%{{.s}}%'	
{{end}}
```
* 这个模板十分简单，有助于我们熟悉了解模板语法，首先用`define`定义了`vlbq`这个sql模板，尾部用`end`结束,模板中的请求参数用双花括号包裹。

* 模板中的`{{.s}}`执行时会替换成实际的请求参数s，也就是`手机`,所以最终执行的sql语句是：
```sql
	select * from vlbq where 名 like '%手机%'
```
* 我们可以在浏览器直接输入`http://localhost:9090/api2/vlbq?s=手机`,来感受一下这个API数据回传。

![](./img/sqlt2.png)

## 模板语法

* sql模板使用了`go语言`的标准库`text/template`进行解析,所有的语法都与标准库兼容，包括标准模板函数。

* 其他模板语法和函数可以百度[golang 模板语法](https://www.baidu.com/s?wd=go语言 模板语法)

## 变量与函数

* 在sql模板里可定义变量和调用一些强大的自定函数，语法是：
```
	{{funcname .arg1 .arg2}}
```

* 例如我们要产生一个新的图片picNo，就可以直接这样写：
```sql
	declare @picNo nvarchar(20)
	
	set @picNo ='{{newpicno}}' --调用ES生成新图号'P0000000x'，后续可直接用@picNo
	
	select @picNo
```
* 上面语句使用了sql原生变量，当然我们也可以用模板变量：
```sql
	{{$picno := newpicno}} 	--后续可直接使用{{$picno}}

	select '{{$picno}}'
```

## *常用函数<span style="color:red">(高级)</span>

|函数名称|类型|说明|
|:----:|:--:|:--|
|and|标准|and 条件|
|not|标准|not 条件|
|or|标准|or 条件|
|range|标准|子项遍历|
|uuid|ESAP|唯一机器编码，类似GUID|
|newrcid|ESAP|调用GetNewId_s获取ES新rcid|
|newpicno|ESAP|调用GetNewId_s获取ES新picNo|
|newlinkno|ESAP|调用GetNewId_s获取  ES新linkNo|
|rtid|ESAP|传入模板名称获取rtid|
|get|ESAP|发起一个get请求，get(url)|
|getbody|ESAP|发起一个get请求，返回body字节，getbody(url)|
|post|ESAP|发起一个post请求,post(url,body)|
|token|ESAP|从token服务器获取某个应用的access_token,token(appname)|
|map|ESAP|传入键值对，制作map,主要用于发送post请求时的body构建|
|mapset|ESAP|为map设置一个值，mapset(map,key,val)|
|str2map|ESAP|传入json文本，得到一个解析的map结果,主要用于钉钉审批解析|
|base64|ESAP|主要用于图片的base64编码|
|md5|ESAP|计算字符串的md5|
|rand|ESAP|生成随机字符串 randstring(strlen)|
|time|ESAP|生成当前Unix时间戳|
|body|ESAP|主要用于url转成图片byte，以便用于后面的AI解析等|
|strjoin|ESAP|string数组转普通string|
|isju|ESAP|判断数据库是否为JU/NX|
|ises|ESAP|判断数据库是否为ES|
|dbtype|ESAP|返回数据库的自定义类型|
|addpic|ESAP|插入指定url的图片到特定表单字段，下载图片到网盘，原型是 DownloadPic(picUrl, tableName, fieldName, rcid, picNo)|
|addlink|ESAP|插入指定url的文件到特定表单字段，下载文件到网盘，原型是 DownloadFile(picUrl, filename, tableName, fieldName, rcid, linkNo)|
|int64date|ESAP|将日期戳转换成日期，主要用于微信审批同步的日期处理|
|int64datetime|ESAP|将日期戳转换成日期时间，主要用于微信审批同步的日期+时间处理|
|getwechatname|ESAP|根据微信userid获取姓名|
|checktableid|ESAP|从dbs的table中查某id是否存在，原型是CheckTableId(dbs, table, field, value)|
|gettablevalue|ESAP|从dbs的table表中根据cond=value查询ret字段值，原型是GetTableValue(dbs, table, cond, ret, value)|
|linkname|ESAP|使用linkno换取附件名|
|sendtext|ESAP|发送消息，原型是SendMsg(appname, touser, content)|
