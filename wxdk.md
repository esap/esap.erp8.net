# 微信打卡
* 2.8版开始，新增微信打卡同步计划，可将微信打卡内容直接存入ES`微信打卡`表单。

* 该功能属于测试阶段，默认不开启，请自行配制task.json进行开启，同时配置esap.yml的agents的`3010011`应用sercet。

## 开启企业微信审批
* 登陆进入【企业微信】-【企业应用】-【打卡】，记录下AgentId和Secret。

![](./img/wxdk.png)

## 修改esap配置文件
* 修改esap.yml，填入上面的应用AgentId和Secret。

![](./img/wxdk2.png)

## 开启esap同步计划
* 修改task.json,开启`微信打卡`计划。默认周期为1分钟，便于调试，生产环境建议周期40分钟。

![](./img/wxdk3.png)

* 重启esap,打卡记录就会同步到ES的`微信打卡`模板了。

![](./img/wxdk4.png)
