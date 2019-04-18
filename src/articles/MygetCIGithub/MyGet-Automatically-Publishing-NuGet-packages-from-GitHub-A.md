# 通过 Myget 从 GitHub 持续集成发布 Nuget 包-A

> 本文推荐阅读地址：https://www.52abp.com/BlogDetails/8

通过 myget 快速体验持续集成功能，从而实现管理自己的开源项目。
52abp.com 所做的很多开源组件，都需要进行 nuget 包的管理和发布，正好我们也在做微信端的集成，所以就把这个系列写一写了。
这次作为说明的开源组件，是`yoyo-abp-modules`里面集成了.net core 版本的 log4net 和微信端的众多组件，内容组件一致在持续更新和增加中。

- 源代码[地址](https://github.com/52ABP/yoyo-abp-modules)：https://github.com/52ABP/yoyo-abp-modules
- Nuget 地址：https://www.nuget.org/profiles/52abp
- Myget 地址：https://www.myget.org/feed/Packages/52abp

我尽量系统性的讲解下 如何从 Github 自动编译和发布到 Nuget 以便有更多人使用。
我自己评估的时候，有 Jenkins 和 myget 等选择。都可以，个人建议开源内容，使用免费的，因为更为稳定。
整体来说，发布一个开源项目到 Nuget 还是很方便的。

> `yoyo-abp-modules`，持续更新中，欢迎使用 ABP 框架的同学来一起使用和完善，期待大家给我们 `star`打星 😍

# 准备工作

感谢[Bil Simser](https://weblogs.asp.net/bsimser)的推文，不过推文是 2014 年的了，是时候更新下内容了，给我的思路，吐槽下 Myget 的官网对我来说，真心不友好，当然，也有可能是我英文太菜了。

准备工作如下：

- 准备一个 GitHub 的仓库,我准备的是[yoyo-abp-modules](https://github.com/52ABP/yoyo-abp-modules)。BitBucket 也支持，我在这里会说明 GitHub。你可以查看[MyGet 文档](https://docs.myget.org/)，了解更多。
- 准备一个[MyGet](https://www.myget.org/)帐户。这个是免费且注册很轻松，他们今年还改版了，笑。
- 一个[NuGet 帐户](https://www.nuget.org/)。现在需要使用 Microsoft 账号作为登录，所以你需要一个微软的账号 。

## MyGet 开始动手

MyGet 是一个 Secure DevOps 从安全的通用软件包管理
构建服务，漏洞扫描和许可证合规性开始，以实现安全的 DevOps 自动化。
提供的方式是开源免费，私有收费的模式，也支持本地化的部署，当然他的特点是 本地化私有部署，功能比 nuget 强大的多。

### MyGetFeed 处理

首先我们要创建属于一个自己的`MyGet Feed`包，可以参考下图来进行创建，在您头像旁边的顶部栏和首页右侧菜单都可以创建独立的 Feed。
![image.png](https://upload-images.jianshu.io/upload_images/1979022-0d342419de7ae66f.png)

![image.png](https://upload-images.jianshu.io/upload_images/1979022-a6c36c7172f2f777.png)
接下来我们创建属于自己的“Feed”包‘52ABP’，写上我们的描述。同时会生成唯一的 URL 地址，这个会提供给你私有的地址信息。

![image.png](https://upload-images.jianshu.io/upload_images/1979022-7adef80dda0cad0a.png)

关于 Feed 版本说明，它分为三个版本：
**This is a public feed 公共版本，相对开放**
每个人都可以从此 Feed 中搜索和下载包，只有管理员可以进行修改包的信息。

**This is a community feed 社区版本，无限开放**
每个人都可以从此 Feed 中搜索和下载包。此外，任何用户都可以在此 Feed 上推送和管理自己的包，可以理解为公共的广场，所有人都可以处理。

**This is a private feed 私有版本，需要进行收费服务**
没有人可以访问。我将邀请能够访问此 Feed 的用户。

### 获取源代码

单击“添加源”按钮以完成设置。创建 Feed 后，您将转储到程序包的主页面，您可以在其中选择各种设置来配置程序包源。默认情况下没有任何东西，所以我们将构建我们的包。
![image.png](https://upload-images.jianshu.io/upload_images/1979022-d9031097ef1469f5.png)

在这里，您可以看到可以添加 GitHub 存储库，BitBucket，Visual Studio Online 服务（或者您可以手动添加一个自己的私有地址信息）。

我们选择使用 GitHub 仓库，仓库地址：https://github.com/52ABP/yoyo-abp-modules

选择`GitHub`，您将被要求授权 MyGet 与 GitHub 交互（如果没有登录会被要求登录 GitHub）。**一旦您授权它，授权的时候请注意如果是组织，请授权给组织，否则选择项目的时候无法看到组织中的项目**，您将在 GitHub 上显示一个存储库列表，您可以从中进行选择。通过单击链接选择您要构建包的那个？

选择复选框并单击“添加”（下面的某些存储库被遮挡但您的存储库不会被遮挡）。

![image.png](https://upload-images.jianshu.io/upload_images/1979022-94d8594c76455e49.png)
然后进入编译

![image.png](https://upload-images.jianshu.io/upload_images/1979022-7a35467bb446a2e0.png)

## Webhooks 钩子

在存储库中的 GitHub 上，转到“设置”，然后单击“Webhooks 和服务”。单击添加 webhook 以显示此对话框：

![image.png](https://upload-images.jianshu.io/upload_images/1979022-ad49e1ce236dc1d7.png)

Payload Url 的来源于 MyGet 的`Hook (HTTP POST):`的 URL 链接。将 Content 类型保留为`application/json`，单击按钮触发器以解决推送事件，然后单击 Add webhook。
这样带来的好处是我们的 commit 一旦提交的时候，就可以自动触发 Myget 的构建环境，生成自己的独立 Myget 包文件。

还可以从 Status badge:中，选择 Copy Markdown ，取得 [[图片上传失败...(image-cb80d-1545973400619)]](https://www.myget.org/)当前仓库的构建状态信息。

通过点击 Edit 按钮，我们可以自定义版本号有关的信息，而且 Myget 的版本号是可以和 github 的 tag 标记互通。
![image.png](https://upload-images.jianshu.io/upload_images/1979022-d5c1b26b53fef2ff.png)

构建完毕后回到`Package`菜单栏
![image.png](https://upload-images.jianshu.io/upload_images/1979022-dbc714b3a2a169a2.png)
可以看到我们自动构建出来的属于自己的 Nuget 包文件。

## 如何使用呢

现在我们有了属于自己的包，我们可以将它添加到`Visual Studio`中的包源并安装它。
这样带来的好处是，我们是使用`Myget`作为自己的个人存储库的角度来使用的，有一定的私有化，我们在将他们发布到 Nuget.org 作为公众服务之前，我们可以使用 MyGet 上的默认（和免费）版本,还可以继续将预发布版本推送到 MyGet，直到您对它满意为止然后将其“推广”到 NuGet。

在 MyGet 中,从菜单中选择 Feed Details。你会看到这样的界面：
![image.png](https://upload-images.jianshu.io/upload_images/1979022-dd4aadb9ff9620a2.png)

我们打开自己的 Visual Studio 2017 ，注意你的版本哦。VS2015 不支持 API 哦。
从`工具`选择 Nuget 包管理器，然后选择涉虚报管理器设置，点击右上角的加号，然后输入好对应你的 API 信息哦~
![image.png](https://upload-images.jianshu.io/upload_images/1979022-fd47288ef406403e.png)
记得点击`更新`，保存好我们的配置文件。
![image.png](https://upload-images.jianshu.io/upload_images/1979022-b36a9268647c6b54.png)

在`包管理器设置`中，将其添加为包源。我只是在开发和测试包时添加它然后禁用它（因此它不会与“官方”NuGet 服务器混淆）。您可以通过这种方式轻松地在私有包和公有包之间来进行切换。
![image.png](https://upload-images.jianshu.io/upload_images/1979022-eff9d6678414eff1.png)

测试下，打开解决方案，Nuget 包管理，然后选择数据源为`myget_52abp`，搜素 yoyo，可以看到对应的版本内容信息。
![image.png](https://upload-images.jianshu.io/upload_images/1979022-22ff21a521421f7c.png)

## 小总结

以上就是我们使用 Myget 通过拉取 github 仓库源代码来进行编译属于自己的 Nuget 包，内容
下一篇我们来讲如何推送到 Nuget.org 服务器中，让所有人都能够使用。

## 期待您参与协作开发

【本文的原文在 github，如果您发现了错漏，欢迎参与协同哦~】

协同地址：(https://github.com/52ABP/Documents/blob/master/src/articles/MygetCIGithub/MyGet-Automatically-Publishing-NuGet-packages-from-GitHub-A.md)

我们创建的 52ABP 框架，已经开始有很多小伙伴开始使用了。如果您对这套基于.net core +angular 的前后端分离的框架感兴趣的话，欢迎来找我们哦~

传送门： [2019 年起如何开始学习 ABP 框架系列文章-开篇有益](https://www.52abp.com/Wiki/52abp/latest/docs/Introduction)
