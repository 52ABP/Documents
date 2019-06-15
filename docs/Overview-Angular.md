 # [52ABP-PRO 前后端分离架构概述](Overview-Angular.md)

> 本文作者：52ABP开发团队 </br>
> 文章会随着版本进行更新，关注我们获取最新版本 </br>
> 本文出处：[https://www.52abp.com/wiki/52abp/latest](https://www.52abp.com/wiki/52abp/latest) </br>
> 源代码： https://www.github.com/52abp </br>


## 介绍
 
 在阅读本文档之前，建议您先运行一次52ABP项目程序，打开了AngularUI 界面,可以参考[快速入门文档](Getting-Started-Angular.md)。 或者你已经对ABP有过一些了解了。
 那么您阅读本篇文档的时候将会更加容易理解这些概念。

## IDE工具和操作系统

我们推荐您使用 [Visual Studio 2017(v15.9.0+)](https://visualstudio.microsoft.com/zh-hans/vs/older-downloads/)以上版本的工具来进行开发。
当然您也可以选择您喜欢的其他工具如：VsCode或者Rider。
因为 .NET Core是跨平台的，所以您可以在任何操作系统中进行运行（MacOS/Linux/Windows)。
 
## 总体设计架构

我们先来看下总体设计架构。
![Overview-Angular-1](images/Overview-Angular-1.png)


Angular UI项目一个可单独部署的项目，它不依赖于后端ASP .NET Core，不用强制部署在一起。
在部署服务的时候，不用考虑他们必须在一台服务器上，只需要在部署的时候，指定好对应的IP或者域名以及端口号。就可以部署成功。

因为当Angular项目被部署出来的时候，它实际上是一个HTML+JS和CSS的网站，它可以在任何的操作系统和Web服务器上提供服务。

需要注意的是，我们的ASP.NET Core解决方案中没有任何HTML、JS和css代码，因为它是基于token的身份验证，而服务之间的通讯都是通过（RESE）风格的API。


## 服务器端多层架构解决方案说明

当您创建一个项目后，打开项目解决方案方案后，可以看到下图所示：

![Overview-Angular-2](images/Overview-Angular-2.png)


解决方案中有7个项目：

- **Application**类库为应用层，主要包含Dto和动态webapi以及应用服务，我们的业务逻辑基本都在这里。
- **Core**层为领域层，包含**实体**和**领域服务**以及枚举（enums）常量等帮助类文件。
- **EntityFrameworkCore**层为基础设施层，包含了项目的DbContext，仓储扩展和实现、数据库的迁移和EF Core中的基本配置信息。
- **Web.Core** 项目主要是服务于MVC和Host项目的公共类文件。
- **Web.Host** 项目不包含任何与Web相关的文件，如Html、Css或Js。它是作为提供远程Webapi的应用程序。因此，您的任何设备都可以来访问您的API应用程序。要了解更多的信息，请参考[Web.Host项目介绍](Features-Mvc-Core-Web-Host-Project.md)
- **Web.Portal**是一个独立的web应用程序，可用于为您的应用程序创建公共页面或登录页面，如52ABP.Com的门户。有关更多信息，请参见[门户项目介绍](Features-Mvc-Core-Web-Portal-Project.md).
- **Tests** 项目包含单元测试和集成测试。
- **Migrator** 项目是一个运行数据库迁移的控制台应用程序。有关更多信息，请移步[迁移数据库控制台](Migrator-Console-Application.md)

## 应用程序

52ABP-PRO解决方案中包含了三个应用程序：

- 后端API(**Web.Host**):提供RESTAPI的应用程序，不包含任何UI的应用程序。
- 门户网站(**Web.Portal**):这可以用于为您的应用程序创建一个公共网站或登陆页面。
- 迁移工具(**Migrator**):运行数据库迁移的控制台应用程序。

## 基本配置

**appsettings.json** 是.Net Core中的系统配置文件，它在Web.host项目中包含许多设置，其中**ServerRootAddress**, **ClientRootAddress**和**CorsOrigins**三个配置是运行应用程序所必须的：

```json

"AdminServerRootAddress": "http://localhost:6298/",
"WebSiteClientRootAddress": "http://localhost:11805/",
"CorsOrigins": "http://localhost:8080,https://pro.52abp.com/"
```

- AdminServerRootAddress是服务端运行的Web.Host应用程序的地址。
- WebSiteClientRootAddress客户端Angular应用程序的URL地址。
- CorsOrigins则是管理允许哪些Url地址向Web.Host应用程序提出跨源请求的URL。

有关配置Web.host应用程序的详细信息，请查看[Web.Host项目介绍](Features-Mvc-Core-Web-Host-Project.md).


## 多租户

多租户的设计是为了让我们在开发SaaS（软件即服务）应用的时候更加容易。使用这种技术，我们可以部署一套应用而服务于多个客户。
每个租户都有属于自己的角色、用户、设置和其他数据。租户和租户直接的数据是隔离的。

52ABP-PRO的代码支持多租户的开发。默认为开启状态。当然也可以通过[配置来关闭它](Getting-Started-Angular.md#配置多租户)。当您禁用它的时候，所有的多租户的功能都会被关闭。我们会默认开启一个名为“default”的租户。

在多租户的应用中，我们有两种不同类型的透视图：

- 宿主（主机）：管理租户和系统。
- 租户：实际使用这些应用系统功能为此付费的用户。
  
多余多租户应用程序，URL可以包含动态的租户名称（Tenancy_Name）。这种情况下，我们可以将租户名称通过占位符的形式来进行表现，如下所示：

``` json

"AdminServerRootAddress": "http://{TENANCY_NAME}.52abp.com/",
"WebSiteClientRootAddress": "http://{TENANCY_NAME}.app.52abp.com/"

```

而在设置CorsOrigins值的时候，可以使用*来代表允许所有子域进行访问。例如：



``` json
"CorsOrigins": "http://*.app.52abp.com/"

```

在启用了以上之后，我们还推荐您继续使用`{TENANCY_NAME}`作为URL地址作为租户的占位符，那么就需要您在AngularUI项目中配置URL。配置好以上后，52ABP-PRO就可以从URL自动检测当前租户信息。

如果您按照上面的方式配置好了，您还应该将所有子域重定向到您的应用程序。需要进行以下配置：

1. 应该配置DNS将所有子域重定向到静态IP地址。要声明“所有子域”，可以使用通配符如`*.52abp.com`
2. 还需要在IIS中配置静态IP绑定到应用程序。

或许还有其他的办法，但是这个应该是最简单了。欢迎沟通交流。

> 而我们在开发的时候不需要为租户配置子域名，我们可以采用更加简单的方法。我们开启多租户的时候提供了**切换租户**的功能来手动让我们在租户和宿主之间进行相互切换。


## Angular解决方案

52ABP-PRO采用的是[NG-Alian-Pro](https://e.ng-alain.com/theme/pro)作为Angular的前端模板，[购买52ABP-PRO](https://www.52abp.com/Purchase)会自动获得此授权无须再单独购买[NG-Alian-Pro](https://e.ng-alain.com/theme/pro)。

Angular解决方案的入口是`src\main.ts`






















来文档中心了解更多：https://www.52abp.com/wiki/ 

### 微信关注我们不走丢

<img src="https://raw.githubusercontent.com/52ABP/Documents/V0.16/src/mvc/images/jiaoluowechat.png" class="img-fluid text-center " alt="公众号：角落的白板报" style="
    height: 80;
    width: 250px;"/>
