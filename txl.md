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

* 具体实现步骤非常简单，找到sql/esap/task.get使用notepad++进行编辑

* 将其中的`sync.dept`，`sync.user`，`sync.tag`,`sync.taguser`四个模板，指向其他自定义数据表，并保证输出字段一致即可。

* 更改示例：(部门同步改到`我的部门表`，用户同步改到`我的用户表`)

```
{ {define "sync.dept"} }
SELECT name, id, parentid, Order1
FROM 我的部门表
{ {end} }

{ {define "sync.user"} }
SELECT userid, name, mobile, dept, position, Email FROM 我的用户表
{ {end} }
```