# 短信平台
目前支持腾讯云短信平台(每月免费100条)，支持二次开发以对接其他短信平台。

## 申请腾讯云账号
* 点击进入腾讯云:[https://cloud.tencent.com/product/sms](https://cloud.tencent.com/product/sms)

* 申请试用后建立一个应用，例如ESAP，记录下`SDK AppID`和`App Key`。

* 在应用的内容配置中添加`签名`和`模板`，审核通过后即可开始使用。

## 配置ESAP
* 进入ESAP设置页面--其他选项页，将前面申请到的短信应用AppID和AppKey填入并保存。

![](/img/sms.png)

* 进入ESAP设置页面--计划任务选项页，新增一个名为`esap 短信提醒`的任务，开启，保存重启ESAP即可。

![](/img/sms-2.png)

## *数据字典
* 数据库表为`esap_sms`，包含下列字段：

|字段名|类型|说明|
|:----|:--|:--|
|tel|nvarchar(100)|必填，电话号码，100字|
|content|nvarchar(500)|必填，短信内容，必须匹配签名和模板，500字|
|result|nvarchar(100)|系统字段，结果，短信发送结果|
|sid|nvarchar(100)|系统字段，短信id|
|fee|int|系统字段，费用计数，整数|
|id|int|系统字段，整数，系统自动编号|

## 注意事项
content字段需要匹配审核通过的【签名】+【内容】模板，不要有多余空格