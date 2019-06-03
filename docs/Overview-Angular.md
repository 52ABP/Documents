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
 
## 架构

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
"CorsOrigins": "http://localhost:8080,http://127.0.0.1:8080,http://localhost:4200,http://localhost:4201,https://pro.52abp.com/"
 
```
- AdminServerRootAddress是服务端运行的Web.Host应用程序的地址。
- WebSiteClientRootAddress客户端Angular应用程序的URL地址。
- CorsOrigins则是管理允许哪些Url地址向Web.Host应用程序提出跨源请求的URL。

有关配置Web.host应用程序的详细信息，请查看[Web.Host项目介绍](Features-Mvc-Core-Web-Host-Project.md).



来文档中心了解更多：https://www.52abp.com/wiki/ 

### 微信关注我们不走丢

<img src="https://raw.githubusercontent.com/52ABP/Documents/V0.16/src/mvc/images/jiaoluowechat.png" class="img-fluid text-center " alt="公众号：角落的白板报" style="
    height: 80;
    width: 250px;"/>
