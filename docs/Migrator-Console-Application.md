

# 迁移数据库控制台.

> 本文作者：52ABP开发团队 </br>
> 文章会随着版本进行更新，关注我们获取最新版本 </br>
> 本文出处：[https://www.52abp.com/wiki/52abp/latest](https://www.52abp.com/wiki/52abp/latest) </br>
> 源代码： https://www.github.com/52abp </br>

52ABP的项目中都包含了一个迁移数据库的工具，**Migrator.exe**。您可以使用它轻松的创建或者更新您的数据库。运行该应用程序创建/主机和租户数据库迁移。

 ![Migrator-Console-Application-1](images/Migrator-Console-Application-1.png)


迁移工具读取的是它项目中的**appsettings.json**文件中的连接字符串。所以请确保你的配置中的连接字符串是所需的数据库。

在运行后，它会检查数据库是否存在，如果不存在则会创建数据库，如果存在则会进行应用程序数据的迁移。

如果启动了多租户的隔离连接字符串，它会获取租户数据库的连接字符串，并为这些数据库运行迁移。

如果没有专用数据库，或者已经为另一个租户迁移了它的数据库(用于多个租户之间的共享数据库)，它将跳过租户。

您可以在开发或者生产环境中使用此工具在部署时迁移数据库，而不是EntityFramework自己的Migrate命令(它需要一些配置，只能在一次运行中运行单个数据库)。



来文档中心了解更多：https://www.52abp.com/wiki/ 

### 微信关注我们不走丢

<img src="https://raw.githubusercontent.com/52ABP/Documents/V0.16/src/mvc/images/jiaoluowechat.png" class="img-fluid text-center " alt="公众号：角落的白板报" style="
    height: 80;
    width: 250px;"/>

ASP。零包含一个工具,* *移居者。exe * *,轻松地迁移您的数据库。您可以运行该应用程序创建/主机和租户数据库迁移。