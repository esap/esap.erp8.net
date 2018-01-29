# 特性支持
- [多重权限](#多重权限)
- [进入提示](#进入提示)
- [语音查询](#语音查询)
- [文章返回](#文章返回) 
- [扫码查询](#扫码查询)
- [多媒体查询](#多媒体查询)
- [专用查询](#专用查询)
- [菜单查询](#菜单查询)
- [连续查询](#连续查询) <span style="color:red">new!</span>

## 多重权限
用逗号隔开，可用【姓名】，【账号】，【部门】，【应用】随意组合。

## 进入提示
* esap.yml配置entermsg=true

* 企业号应用回调勾选【用户进入提示】

* esap_cx表中的entermsg可写select来作为进入提醒。

![](./img/s2-1.png) 

## 语音查询
<img src="./img/8.13.png" width="240">
<img src="./img/8.14.png" width="240">
<img src="./img/8.15.png" width="240">

 
## 文章返回
* url有值时触发,url可使用参数{\{.pn\}}。

![](./img/wxcx-1.png)
<img src="./img/wxcx-2.jpg" width="240">
<img src="./img/wxcx-3.jpg" width="240">

## 扫码查询
二维码或其他条码等,esap_cx表中的mkey与自定义菜单的扫码弹框菜单key对应即可

<img src="./img/8.16.png" width="240">
<img src="./img/8.6.jpg" width="240">
<img src="./img/8.18.png" width="240">

## 多媒体查询
* sql结果字段或别名为：
 * `pic`或`图片`
 * `files`或`附件`
 * `voice`或`语音`
 * `video`或`视频`

* 支持返回多个`图片`或`附件`

<img src="./img/8.21.jpg" width="240">
<img src="./img/8.22.jpg" width="240">
<img src="./img/mutimedia-2.jpg" width="240">

> 注意微信限制：图片一般不能超过2M,附件不超过20M

<img src="./img/8.24.jpg" width="240">
![](./img/8.23.png)

## 专用查询
* 专用查询字段(app)为配置的某应用名时（appName），查询不再需要关键字引导，该应用也不再响应其他关键字，仅需输入参数就可查询。

![](./img/8.40.jpg)
<img src="./img/8.38.jpg" width="240">

* 专用查询可直接扫二维码秒查。

![](./img/8.42.png)
![](./img/8.41.png)
<img src="./img/8.43.jpg" width="240">
<img src="./img/8.44.jpg" width="240">

## 菜单查询
设置【mkey】，与企业号应用自定义菜单中的key一致。

<img src="./img/8.27.jpg" width="320">
<img src="./img/8.28.jpg" width="320">

## 连续查询
设置【下一步】，接下来的输入必然执行该查询，可多级连续。

<img src="./img/wxcx2-lxcx2.jpg">
<img src="./img/wxcx2-lxcx.jpg" width="320">

* 第一个发起的查询的参数在连续查询中解析为pf0，pf1，pf2...

* 上一次查询的参数在连续查询中解析为pp0，pp1，pp2...