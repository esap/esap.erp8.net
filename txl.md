# 通讯录同步
* 通讯录同步计划，可直接同步本地部门、用户和角色到企业微信，默认不开启，需开启企业微信的编辑通讯录权限。

## 开启企业微信同步权限
* 登陆【企业微信】-【管理工具】-【通讯录同步】，权限选择编辑通讯录权限。

![](./img/txl-1.png)

## 配置esap通讯录应用
* 应用AgentId为9999999（固定7个9），secret为上面的。

![](./img/txl-1.1.png)

## 开启esap同步计划配置
* 建议周期20分钟

![](./img/txl-2.png)

## *自定义通讯录同步[高级教程]
esap允许自定义通讯录查询sql，对接各种系统的组织架构。

#### 具体步骤
* 在计划任务中配置脚本前缀，例如`my.`，然后复制sql/esap/localuser.get文件重命名成`my_txl.get`文件，使用notepad++进行编辑

![](./img/txl-3.png)

* 定义带`my.`前缀的`my.sync.dept`，`my.sync.user`，`my.sync.tag`,`my.sync.taguser`四个模板，指向其他数据表，保证输出字段一致即可。

#### 更改示例
* 部门同步改到`我的部门表`，用户同步改到`我的用户表`

{% raw %}
```sql
{{define "my.sync.dept"}}
	SELECT name, id, parentid, order as Order1 FROM 我的部门表
{{end}}

{{define "my.sync.user"}}
	SELECT userid, name, mobile, dept, position, Email, telephone, isleader, englishname, gender 
	FROM 我的用户表
{{end}}
```
{% endraw %}