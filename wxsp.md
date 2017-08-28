# 微信审批
* 微信审批同步计划可将微信审批内容直接存入本地数据库，并且支持自定义模板。

* 该功能默认不开启，请自行配置开启。

## 开启企业微信审批
* 登陆进入【企业微信】-【企业应用】-【审批】，记录下AgentId和Secret。

![](./img/wxsp.png)

## 开启esap计划任务配置
* 填入上面的应用AgentId和Secret。

![](./img/wxsp2.png)

## 开启esap同步计划
* 默认周期为1分钟，便于调试，生产环境建议周期5分钟。

![](./img/wxsp3.png)

* 重启esap,请假和报销审批记录就会同步到ES的`ESAP_审批`模板了。

## *自定义审批模板同步[高级教程]
* esap强大的sql模板功能，允许用户将自定义审批模板数据同步到sql，并轻松实现ES表单新建。

* 具体实现步骤如下：

* (1) 在企业微信自定义一个审批模板，例如缺勤表。

![](./img/wxsp4.png)

* (2) 在ES中也建立一个审批模板，用于存放记录，例如缺勤表。

![](./img/wxsp5.png)

* (3) 使用notepad++修改sql/esap/wxsp.post,定义一个名叫`缺勤表.wxsp`的`sql模板`，用来连接企业微信与ES，注意`.wxsp`后缀是必须的。

![](./img/wxsp6.png)

* (4) 这样就完成了自定义审批模板的同步设置。

![](./img/wxsp7.png)

## 代码注释
```sql
{ {define "缺勤表.wxsp"} } --定义sql模板【缺勤表.wxsp】
  if not exists (select * from 缺勤表 where spnum=:SpNum)   --检查审批流水号SpNum是否存在，SpNum是`微信审批`系统变量
  begin
	insert
		缺勤表(学号,课程,日期,制表,记录日期,spnum,spstatus,excelserverrcid,excelserverrtid)  --插入主表记录
	select
		'{ {.学号} }',   --对应企业微信的学号，以下带花括号的变量同理
		'{ {.课程} }',
		'{ {.日期} }',
		:ApplyName,   --申请人姓名，微信审批系统变量
		'{ {.制单日期} }',
		:SpNum,       --审批编号，微信审批系统变量
		:SpStatus,    --审批状态，微信审批系统变量
		:rcid,:rtid   --rcid,rtid，esap系统变量
  { {template "repcase"} }    --插入Es_repcase记录，用于ES工作台显示
  end
{ {end} }
```

## 微信审批系统变量全解
```
Spname          // 审批名称(请假，报销，自定义审批名称)
ApplyName       // 申请人姓名
ApplyOrg        // 申请人部门
ApprovalName    // 审批人姓名
NotifyName      // 抄送人姓名
SpStatus        // 审批状态：1审批中；2 已通过；3已驳回；4已取消
SpNum           // 审批单号
Leave           // 请假类型
Expense         // 报销类型
```

## 关于sql模板
更多内容请阅读[SQL模板章节](/sqltpl.md)
