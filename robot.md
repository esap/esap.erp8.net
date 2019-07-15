# 机器人接口

ESAP4.0增加了机器人接口，可以对接各种机器人平台直接服务于企业ERP。

机器人接口地址：`http://esap服务器:9090/robot/`

## 接口示例

请求方法：POST

请求URL示例：`http://192.168.99.10:9090/robot/机器人id?msg=查询内容&userid=用户id&pic=图片url`

该请求会获得与[微信查询](./wxcx.md)一样的效果

查询内容会按逗号或空格被分割为`p1,p2,...pn`

userid被解析为`pu`，图片url解析为`praw`

其他用法参见[微信查询](./wxcx.md)

## QQ机器人插件

ESAP-qqbot机器人插件（支持cleverqq）

* <a href="./build/esap-qq.zip" download target="_blank">esap-qq</a>

## 微信机器人组件

ESAP-wxbot机器人插件（支持微信个人号的群聊私聊）

* <a href="./build/esap-wxbot.zip" download target="_blank">esap-wxbot</a>

## 有度机器人组件(比飞秋更强大)

ESAP-ydbot机器人插件

* <a href="./build/esap-ydbot.zip" download target="_blank">esap-ydbot</a>

## 飞秋机器人组件

ESAP-feiq机器人插件（支持文字查询）

* <a href="./build/esap-feiq.zip" download target="_blank">esap-feiq</a>

## 更多机器人对接

* 可按示例URL自行调用和控制，或者找<a href="tencent://message/?uin=332829166"> 村长 </a>定制