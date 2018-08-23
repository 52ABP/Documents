# Abp 框架中文文档

## 总体介绍

-   [入门介绍](Introduction.md)

-   [多层次架构体系](NLayer-Architecture.md)
-   [模块系统](Module-System.md)
-   [启动配置](Startup-Configuration.md)
-   [多租户](Multi-Tenancy.md)
-   [集成OWIN](OWIN.md)
-   [调试](Debugging.md)



## 公共结构

-   [依赖注入](Dependency-Injection.md)
-   [会话管理(Session)](Abp-Session.md)
-   [缓存管理](Caching.md)
-   [日志管理](Logging.md)
-   [设置管理](Setting-Management.md)
-   [时间与时区设置](Timing.md)
-   [对象之间的映射(AutoMapper集成)](Object-To-Object-Mapping.md)
-   [邮件发送(MailKit集成)](Email-Sending.md)

## 领域层

-   [实体](Entities.md)
    -   [Multi-Lingual Entities <label class="badge badge-secondary badge-success">NEW</label>](Multi-Lingual-Entities.md)
-   [值对象](Value-Objects.md)
-   [仓储](Repositories.md)
-   [领域服务](Domain-Services.md)
-   [规约模式](Specifications.md)
-   [工作单元](Unit-Of-Work.md)
-   [领域事件 (事件总线)](EventBus-Domain-Events.md)
-   [数据过滤器](Data-Filters.md)


## 应用层

-   [应用服务](Application-Services.md)
-   [数据传输对象](Data-Transfer-Objects.md)
-   [数据传输对象验证](Validating-Data-Transfer-Objects.md)
-   [权限验证](Authorization.md)
-   [功能管理](Feature-Management.md)
-   [审计日志](Audit-Logging.md)
-   [实体历史 <label class="badge badge-secondary badge-success">NEW</label>](Entity-History.md)


## 分布式服务层

-   ASP.NET Web API
    -   [Web API 控制器](Web-API-Controllers.md)
    -   [动态WebApi层](Dynamic-Web-API.md)
    -   [集成OData](OData-Integration.md)
    -   [集成Swagger UI](Swagger-UI-Integration.md)
    -   [ASPNET Core 集成OData](5.5ABP分布式服务-ASPNETCoreOData集成.md)


## 表现层

-   ASP.NET MVC
    -   [Mvc控制器(MVC-Controllers)](MVC-Controllers.md)
    -   [MVC视图(MVC Views)](MVC-Views.md)
    -   [Handling Exceptions](Handling-Exceptions.md)
-   ASP.NET Core
    -   [ASP.NET Core Integration](AspNet-Core.md)
    -   [ASP.NET Core OData Integration <label class="badge badge-secondary badge-success">NEW</label>](OData-AspNetCore-Integration.md)
-   [Localization](Localization.md)
-   [导航栏](Navigation.md)
-   [Embedded Resources](Embedded-Resource-Files.md)
-   [Javascript API](/Pages/Documents/Javascript-API)
-   [CSRF和XSRF保护](XSRF-CSRF-Protection.md)

##  后台服务

-   [后台作业和后台工人](Background-Jobs-And-Workers.md)
-   [集成Hangfire](Hangfire-Integration.md)
-   [集成Quartz](Quartz-Integration.md)

## 实时服务

-   [通知系统](Notification-System.md)
-   [集成SignalR](SignalR-Integration.md)
-   [集成SignalR AspNet Core <label class="badge badge-secondary badge-success">NEW</label>](SignalR-AspNetCore-Integration.md)


## 基础设施层(对象关系映射层)

-   [集成EntityFramework](EntityFramework-Integration.md)
-   [集成EntityFramework Core](Entity-Framework-Core.md)
-   [集成NHibernate](NHibernate-Integration.md)
-   [集成Dapper ](Dapper-Integration.md)

## 发布信息

-   [Nuget 包](Nuget-Packages.md)
-   [发布和变更日志信息](https://github.com/aspnetboilerplate/aspnetboilerplate/releases)

## 模块 Zero 文档

## 总体介绍

-   [总体介绍](Zero/Overall.md)
-   Startup Templates
    -   [ASP.NET Core & Angular](Zero/Startup-Template-Angular.md)
    -   [ASP.NET Core MVC & jQuery](Zero/Startup-Template-Core.md)
    -   [ASP.NET MVC 5.x / AngularJS 1.x](Zero/Startup-Template.md)
  
## 功能

-   [多租户管理](/Pages/Documents/Zero/Tenant-Management)
-   [版本管理](/Pages/Documents/Zero/Edition-Management)
-   [用户管理](/Pages/Documents/Zero/User-Management)
-   [角色管理](/Pages/Documents/Zero/Role-Management)
-   [组织单元管理](/Pages/Documents/Zero/Organization-Units)
-   [权限管理](/Pages/Documents/Zero/Permission-Management)
-   [多语言管理](/Pages/Documents/Zero/Language-Management)
-   [集成 Identity Server](Zero/Identity-Server.md)

# 其他说明

本文档发布在  https://www.52ABP.com/wiki/index 

仓库地址：https://github.com/52ABP/Documents

[![GitHub issues](https://img.shields.io/github/issues/52ABP/Documents.svg?style=popout)](https://github.com/52ABP/Documents/issues)
[![GitHub forks](https://img.shields.io/github/forks/52ABP/Documents.svg?style=popout)](https://github.com/52ABP/Documents/network)
[![GitHub stars](https://img.shields.io/github/stars/52ABP/Documents.svg?style=popout)](https://github.com/52ABP/Documents/stargazers)
[![GitHub license](https://img.shields.io/github/license/52ABP/Documents.svg?style=popout)](https://github.com/52ABP/Documents/blob/master/LICENSE)

如果你想为文档做贡献，请遵循以下步骤：
* 如果是一个小的变化（输入错误或语法修正，或者添加一些句子），您可以直接进行并发送一个拉请求。
* 如果这是一个重大的变化（我们建议您创建一个新文档或者在现有的文档中找一个新区域添加内容），
我们建议您创建一个Issue，写出更加详细的描述。
* 我们将评估您所要求的更改。如果它被接受了，你可以讲它变更为PR，我们会合并掉PR。
* 请在当前文件中的遵循相同标准。