# ABP框架开发电话簿应用实例（ASP.NET Core和Angular版本）


> 本文作者：52ABP开发团队 </br>
> 文档会随着版本进行更新，关注[52ABP.com](https://www.52abp.com)获取最新版本 </br>
> 本文出处：[https://www.52abp.com/wiki/52abp/latest/](https://www.52abp.com/wiki/52abp/latest/) </br>
> 源码下载： [https://code.52abp.com/52abp](https://code.52abp.com/52abp) </br>


从本文档开始，我们将使用52ABP-PRO创建一个**电话簿应用**实例的完整开发指南，完成这个内容后，你可以完整的了解**多租户、本地化、授权、可配置项、单元测试**等内容。
 

本文档适用于**ASP.NET Core 后端和Angular UI**前后端分离的项目类型。

 

您还可以通过查看[其他项目类型文档](/docs/Getting-Started.md)。

 
## 开始

[创建并运行一个ABP项目](Angular/1.Creating-Running-Project.md)


## 完整目录

- [创建并运行一个ABP项目](Angular/1.Creating-Running-Project.md)
- [Angular应用中添加一个菜单栏](Angular/2.Adding-New-Menu-Item.md)
- [创建一个前端PhoneBook组件](Angular/3.Creating-PhoneBook-Component.md)
- [在ABP框架中定义Person实体类](Angular/4.Creating-Person-Entity.md)
- [同步Person实体到数据库中创建映射表](Angular/5.Database-Migrations-Person-Entity.md)
- [在ABP框架中创建Person的应用服务](Angular/6.Creating-Person-Application-Service.md)
- [ABP框架中为Person应用服务创建单元测试](Angular/7.Creating-Unit-Tests-for-Person-Application-Service.md)
- [在Angular组件中实现查询People的方法](Angular/8.Using-GetPeople-Method-from-Angular.md)
- [如何在ABP框架中添加一个联系人信息](Angular/9.Creating-New-Person-Method.md)
- [在ABP框架中使用单元测试Xunit测试添加方法](Angular/10.Creating-Testing-Create-Person-Method.md)
- [在Angular客户端创建一个模态框完成添加联系人功能](Angular/11.Creating-Testing-Creating-Modal-New-Person.md)
- [ABP框架中为我们的电话薄应用程序添加权限验证内容](Angular/12.Authorization-PhoneBook.md)
- [在ABP框架中完成删除联系人功能](Angular/13.Deleting-Person.md)
- [模糊搜索联系人信息](Angular/14.Filtering-People.md)
- [在ABP框架中实现一对多的关联关系](Angular/15.Creating-Phone-Entity.md)
- [针对Phone实体信息的数据库迁移](Angular/16.Migrations-Phone-Entity.md)
- [在ABP中的多表联动查询的实现](Angular/17.Changing-GetPeople-Method.md)
- [给PersonApplicatonService应用服务添加电话和删除电话两个方法](Angular/18.Adding-AddPhone-DeletePhone-Methods.md)
- [添加并查看联系人的电话信息](Angular/19.Edit-Mode-Phone-Numbers.md)
- [完成编辑联系人信息](Angular/20.Compleate-EditPerson.md)
- [如何改造既有功能让它支持多租户功能](Angular/21.Multi-Tenancy.md)
- [运行应用程序验证多租户下的数据隔离](Angular/22.Running-Application.md)
- [52ABPPRO源代码下载和总结](Angular/23.Develop-Angular-The-End.md)



我们需要创建并下载名为**YoyoSoft.PhoneBookDemo**的解决方案，可参考[快速启动52ABP——Pro项目](../Getting-Started-Angular.md)文档。
