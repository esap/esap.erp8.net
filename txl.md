# 通讯录同步
* 通讯录同步计划，可直接同步ES部门、用户和角色，该功能默认不开启，使用时需开启企业微信端的编辑通讯录权限。

## 开启企业微信端同步接口
* 登陆【企业微信】-【管理工具】-【通讯录同步】，权限选择编辑通讯录权限。

![](./img/txl-1.png)

## 开启esap同步计划配置
* 建议周期20分钟

![](./img/txl-2.png)

## *自定义通讯录同步[高级教程]
* esap强大的sql模板功能，允许用户自定义通讯录表，从而实现任何基于sql的系统组织架构同步。

* 具体实现步骤非常简单，在admin中配置脚本前缀，例如`fabe.`，然后在sql/esap目录下建立自己的*.get脚本，例如fabe_txl.get,使用notepad++进行编辑

* 在其中建立带`fabe.`前缀的`fabe.sync.dept`，`fabe.sync.user`，`fabe.sync.tag`,`fabe.sync.taguser`四个模板，指向其他自定义数据表，并保证输出字段一致即可。

* 更改示例：(部门同步改到`我的部门表`，用户同步改到`我的用户表`)

```
{ {define "fabe.sync.dept"} }
SELECT name, id, parentid, Order1
FROM 我的部门表
{ {end} }

{ {define "fabe.sync.user"} }
SELECT userid, name, mobile, dept, position, Email FROM 我的用户表
{ {end} }
```