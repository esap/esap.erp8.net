# 部署ESAP服务
在生产环境中，esap可以使用nssm封装为服务，从而实现开机自动运行和崩溃自动重启。

* [安装服务](#安装服务)
* [配置自启](#配置自启)
* [卸载服务](#卸载服务)
* [服务升级](#服务升级)

## 安装服务
* 下载nssm2.24把`nssm.exe`放到任意目录(例如C盘根目录)。

* 运行cmd，运行`nssm install`命令，进入设置界面,选择`esap.exe`，填写服务名称，例如:`appEsap`

![](/img/dep-1.png)

* 在`Details`页添加服务描述，此项可选。

![](/img/dep-2.png)

* 在`I/O`页添加日志文件路径，事先新建一个`log.txt`，此项可选。

![](/img/dep-3.png)

* 设置日志文件后可以设置日志文件的生成方式，例如下图为每次启动服务后转存一份，此项可选。

![](/img/dep-4.png)

* 点击`install service`完成服务安装。

![](/img/dep-5.png)

## 配置自启

* 进入windows管理工具-服务，找到`appEsap`服务(a开头比较靠前啦^_^)，右键进入属性。

![](/img/dep-6.png)

* 在恢复页面设置失败重启和重置计数后，点击确认即可。

![](/img/dep-7.png)

## 卸载服务
同样进入cmd，运行`nssm remove`，填入`appEsap`，点击`remove service`即可。

![](/img/dep-8.png)

## 服务升级
* 封装成服务后，要升级新版esap，需先进入管理工具-服务，找到`appEsap`，右键停止服务。

* 然后，替换新版`esap.exe`，再次重启服务即可。