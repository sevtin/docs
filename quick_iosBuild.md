# iOS 项目构建

页面导航：

- [ 环境准备 ](#ios_build_envir)
- [ 创建 Flow ](#ios_create_flow)
- [ 触发构建 ](#ios_build_trigger)
- [ 获取产物 ](#ios_get_ipa)

### <a name="ios_build_envir">1、环境准备</a>

* 安装 Fastlane

 - 目前 Flow.ci 尚处于 Beta 版本，没有完全集成 Fastlane，需要用户手动在 Agent 机器上安装 Fastlane，参见：https://docs.fastlane.tools/getting-started/ios/setup/

* 导入证书

 - 参见：[如何找到 Provisioning Profiles & 证书文件](./other_p12.md)

* 编写 yml 配置文件并上传到 Git 项目根目录

 - 在根目录下添加 .flow.yml 文件。

 - 对于新创建的项目，Flow.ci 会在根目录下自动查找 .flow.yml 项目配置文件，根据配置文件中定义的步骤，自动生成工作流。

如何编写 yml 配置文件请参见：[iOS 模板](./yml_ios.md)

### <a name="ios_create_flow">2、创建 Flow</a>

<img src="https://images-cdn.shimo.im/GuKjruYMv3k84gRu/iosbuild_1.jpg" style="zoom:30%">

环境准备完成后，打开 Flow.ci Web，点击创建 Flow  按钮（图1）打开 “创建 Flow” 界面，填写 Flow 名称后进入 “配置 Git 仓库”，如 <图2>。

图2

<img src="https://images-cdn.shimo.im/5WAdLECC6usRM8sd/iosCreateProj.jpg" style="zoom:30%">

这里我们选择 “SSH” 方式连接 Git 仓库并且输入项目 “Git 仓库地址” 。

Flow.ci 触发自动构建需要接收 Git 仓库的 webhook 事件，所以需要 “手动添加 webhook 地址到你的 Git 仓库”，添加方式如下：

在 GitHub 中打开你的项目，然后依次点击 “Settings” - “Webhooks” - “Add webhook”。

图3

<img src="https://images-cdn.shimo.im/ik4ER7hszvw2b0NZ/addwebhook.jpg" style="zoom:30%">

在 “Payload URL” 中输入 webhook 地址，并选择 “Content type” 为 application/json。

推荐修改触发 webhook 的事件为 Push & PullRequest，不使用默认的 “Send me everything”。

最后点击 “Add webhook” 按钮完成创建。

回到 Flow ci “配置 Git 仓库” 界面，点击 “连接测试” 按钮，测试是否成功连接 Git 仓库。测试成功后，点击 “完成” 按钮，完成 Flow 创建。

### <a name="ios_build_trigger">3、触发构建</a>

图 4

<img src="https://images-cdn.shimo.im/AYFaRGIyccUIbiwv/iosrunbuild.jpg" style="zoom:30%">

创建 Flow 成功后，有两种方式触发项目构建：

* 修改项目任一文件并提交，触发构建

* 手动点击 “运行工作流”

点击打开构建详情，可查看构建日志等信息。

图 5

<img src="https://images-cdn.shimo.im/tO03tDIS7MYAY07H/iosbuildlog.jpg" style="zoom:30%">



### <a name="ios_get_ipa">4、获取产物</a>






<br/><br/><br/>

<div id="bom">
<a href="./admin_plugin.md">上一节：插件管理 </a> |
<a href="./admin_credentials.md">下一节：证书管理 </a>
</div>

<link rel="stylesheet" rev="stylesheet" href="flow.css" type="text/css"/> 