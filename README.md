<p align="center">
  <img src="./img/logo.png" width="120">
</p>

## ES最佳实践
凝聚ERP高级开发实践经验和持续成果的免费项目——ESAP，来自村长的倾情奉献!

#### [快速开始](s0.md)

##### 最新版本
* <a href="./build/esap2.6beta7.rar" target="_blank">v2.6beta7.rar </a><span style="color:red"> new!</span>

##### 历史版本
* <a href="./build/esap2.5x86.rar" target="_blank">v2.5x86</a>

* <a href="./build/esap2.5x64.rar" target="_blank">v2.5x64</a>

##### 文档&源码

* 文档源码(Github)：[https://github.com/esap/esap.erp8.net](https://github.com/esap/esap.erp8.net) 

* 欢迎提需求，[玩家需求实现进度](ref.md)

##### ES模板

* 微信模板(支持ES9.4+): <a href="./db/wechat_tmp.rar" target="_blank">wechat_tmp</a> <span style="color:red">plus!</span>

* 邮件提醒(支持ES9.2+): <a href="./db/email_tmp.rar" target="_blank">email_tmp.rar</a> 

##### 示例数据库

* <a href="./db/esap2.0.rar" target="_blank">v2.5</a> <span style="color:red">plus!</span>

> ES 9.4.124; SQLSERVER 2008R2

#### 捐赠
维护这个项目需要大量时间和精力，如果它确实帮上了你的忙，不要忘了请我喝杯茶哦 :)

<p align="center">
  <img src="./img/esap_pay.png" width="400">
</p>

<hr />

#### 更新日志

##### v2.6
内测中

* 使用vux重写app；
* 使用sqlt重写微信提醒插件,支持自定义sql模板；
* 使用sqlt重写微信超级查询应用,支持自定义sql模板；
* 使用sqlt重写api模块,支持自定义sql模板；
* 新增ESWEB待办事宜列表打开；
* 超级查询新增用户进入时显示可用查询列表功能，企业号端需开启上报用户进入；
* 超级查询新增ES表单搜索查看功能；
* 超级查询优化消息机制，改善网络延迟造成的重发问题；
* 增加admin查询管理模块(/admin)；
* 超级查询增加打包回复模式（mediaOnly=3）；
* 取消`微信通讯录`模板，改为服务器缓存，解决重名和同步等烦恼；
* 微信提醒接收人填报更自由，可使用姓名，账号，手机号，微信号，邮箱，职位，部门任意组合搭配；
* HOST配置支持端口，可以与监听端口(例如9090)不一致，更方便外网NAT；
* 重构ESAP主容器，采用模块化+插件化架构，适应大规模开发定制应用；
* 修复中文消息超过500字时拆分出空消息的bug；

##### v2.5 里程碑！
发布于`2017-3-8`

* 微信提醒新增图片、文件消息支持；
* 微信提醒新增多人多部门消息支持；
* 微信提醒新增密图文消息支持，支持多条密图文；
* 微信提醒新增普通新闻消息支持，支持多条普通新闻；
* 新增微信签到，支持地图显示，支持菜单按钮签到；
* 新增微信图库，通过相册或拍摄照片上传，支持多图上传；
* 新增微信反馈，通过APP进行反馈提交；
* 微信超级查询新增回写支持，支持update,insert；
* 微信超级查询新增通讯录变量支持，增加任意标点分割功能；
* 微信超级查询新增多选混合权限支持；
* 微信超级查询新增任意应用回调支持；
* 微信超级查询新增扫码(二维码/条码)查询支持；
* 微信超级查询新增图片，附件查询支持；
* 微信超级查询新增OCR接口；
* 微信超级查询增加自动拆分消息功能(500字)；
* 微信超级查询增加填报功能； <span style="color:red">plus!</span>
* 增强办理链接加密级别； <span style="color:red">plus!</span>
* 增强微信图库兼容级别； <span style="color:red">plus!</span>
* 修复超级查询随机排序问题；
* 采用echo框架重构公共库。

##### v2.4 plus！
发布于`2017-2-4`

* 新增微信超级查询引擎；
* 新增API主机(Host),ESweb主机配置项；
* 新增工作流办理； <span style="color:red">plus!</span>
* 采用重构版微信SDK。 <span style="color:red">plus!</span>

##### v2.3
发布于`2017-1-18`

* 新增微信提醒标题配置项；  
* 新增邮件提醒功能，可带图片、附件；  
* 修复高版本网盘系统表切换问题。

##### v2.2
发布于`2017-1-13`

* 简化配置项，增加配置页面/conf；  
* 更新大量细节，模块运行更稳定；
* 错误提示完善，不再因普通错误导致崩溃；  
* 现在你只需要两步就可以玩转微信提醒： **1、导入模板；2、启动esap.exe** 就是这么简单！

##### v2.1
发布于`2017-1-7`

* 修复BOM复制本表代码；  
* 更新vBOM、vPBOM视图，修复子件超过10个的RN排序问题；  
* 导入微信提醒、微信通讯录、微信提醒视图(vwxtx)；    
* 增加微信企业号API及基本配置； 

##### v2.0 
发布于`2017-1-5`

* 导入主数据：商品、企业、字典；  
* 导入IO单对象、订单对象；  
* 导入无级BOM；  
* 导入自动检查更新功能(ESAP_关于)。
