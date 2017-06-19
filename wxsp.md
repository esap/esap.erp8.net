# 微信审批
* 2.8版开始，新增通讯录同步计划，可直接同步ES部门和用户，该功能属于测试阶段，默认不开启，请自行配制task.json进行开启，同时配置txlsercet为通信录sercet，并开启编辑通讯录权限。

## 开启企业微信端同步接口
* 登陆【企业微信】-【管理工具】-【通讯录同步】，权限选择编辑通讯录权限。

![](./img/txl-1.png)

## 开启esap同步计划
* 修改task.json,开启`增量同步ES组织`计划，建议周期20分钟

![](./img/txl-2.png)

## *自定义通讯录同步[高级教程]
* esap强大的sql模板功能，允许用户自定义通讯录表，从而实现任何基于sql的系统组织架构同步。

* 具体实现步骤非常简单，找到sql/get/task.tpl使用notepad++进行编辑

* 其中的`sync.dept`，`sync.user`两个模板，指向其他自定义数据表，并保证输出字段一致即可。

```
{ {define "sync.dept"} }
SELECT DeptName name		--部门名称
	,DeptId id		--部门id
	,isnull(SuperId,1) parentid		--上级id
	,10000-floor(right(Path,2)) as Order1		--排序，越大越靠前
FROM ES_Dept
where DeptId>1
{ {end} }

{ {define "sync.user"} }
SELECT
	UserLogin userid		--用户账号，唯一
	,UserName name		--用户姓名
	,mobilephone mobile		--用户手机，唯一
	,DeptId dept		--用户部门id
	,roleNames position		--用户职位
	,Email		--用户Email
FROM ES_User
{ {end} }
```

* 更改示例：(部门同步改到wxdept表，用户同步改到wxtxl表)

```
{ {define "sync.dept"} }
SELECT name, id, parentid, Order1
FROM wxdept
{ {end} }

{ {define "sync.user"} }
SELECT userid, name, mobile, dept, position, Email FROM wxtxl
{ {end} }
```