<p align="center">
  <img src="./img/logo.png" width="120">
</p>

# ESAP起源

### 什么是ESAP
* ESAP的全称是`Eden Solution and Products`，旨在打造殿堂级的信息化产品和解决方案。

* ESAP起源于2012年，最初由勤哲Excel服务器（ES）实现的，后来又借鉴汲取了著名的ERP系统——`SAP R3`的架构思想进行了重构。因此拥有了ES的灵活与SAP的强大。

* ESAP在过去的6年积攒沉淀了许多优秀的思想和技术，包括：2012年，实现了模板级导航并用于生产；2015年，配合golang实现了与微信对接；2017年，实现了百度AI，腾讯云，阿里云等多种云服务集成。

### ESAP项目构成
ESAP拥有一套完整的独立生态，现在ESAP主要包括以下模块：

#### ESAP-API
对接SQL的restfulAPI容器，无需任何二次开发，只要写写sql模板即可快速堆建你的专用数据API，已公开发布。
> URL示例：`http://ESAP服务器IP:9090/api2/action`

#### ESAP-APP
提供ESAP移动端的访问，ESAP-APP采用了当下流行的Vue组件构建前端，提供了迅速定制实现任何复杂UI的可能，demo源码开源在https://github.com/esap/app
> URL示例：`http://ESAP服务器IP:9090/app`

**[在线示例体验](https://erp8.net/m/)**

#### ESAP-Admin
提供ESAP管理端的访问，公开发布，源码开源在https://github.com/esap/admin
> URL示例：`http://ESAP服务器IP:9090/admin`

#### ESAP-WebServer
提供专门设计的Webserver，模块化+插件式开发，动态编译，不依赖IIS，部署简单，工程化，一个配置文件(esap.yml)搞定动态加载启动，已公开发布。

#### ESAP-Desktop
高级桌面端B/S架构，定制实现各种特殊需求，例如打开门禁，连接地磅，或者是连接PLC显示生产线实时数据。

**[在线示例体验](https://demo.esap.vip)**

#### 微信API
* 对接`企业微信、企业号`的API，提供企业号应用接口功能，实现用户与ES对话式的交互，已公开发布。

> 回调URL示例：`http://ESAP服务器IP:9090/wx/应用名`

* 对接微信`订阅号、服务号、小程序`的API，提供回调接口功能，实现用户与ES对话式的交互，已公开发布。

> 回调URL示例：`http://ESAP服务器IP:9090/wxs/应用名`

#### ESAP主库
驱动ESAP微信应用的主数据库，已发布。

#### ES-API
对接ES，JU库的专用API，不同于ESWEB，ES-API除了提供ES，JU数据访问、还提供图片、附件访问，甚至包括官方没有的缩略图等接口功能，已公开发布。
> URL示例：`http://ESAP服务器IP:9090/es/action`

** 尽管看起来模块非常多，实际部署时仅仅只需要运行esap-cli，再登陆admin模块配置一下就可以了，就是这么简单! **

### ESAP的哲学
`Easy Simple And Powerful`，简单就是美，这个借口可以用一万年!

### ESAP的未来
持续集成的社区力量，思想有多远，我们就能走多远。
