
### 下载起始模板

下载 **ASP.NET CORE** 和 **Entity Framnework Core** 的起始模板以集成MySQL。
本文档将介绍[使用**ASP.NET Core 2.x**+**.NET Core Framework** + **身份验证**的多页模板](https://aspnetboilerplate.com/Templates)。

### 准备开始

微软官方文档中提到了两个用于MySQL的实体框架核心提供程序。其中一个是[官方 MySQL EF核心数据库提供程序](https://docs.microsoft.com/en-us/ef/core/providers/mysql/)，另一个是[用于MySQL的Pomelo EF核心数据库提供程序](https://docs.microsoft.com/en-us/ef/core/providers/pomelo/)。

> **注意:** 官方提供程序尚不支持EF Core 2.0，因此将在此示例中使用Pomelo EF核心数据库提供程序。
> 
> 相关问题: https://github.com/aspnet/EntityFrameworkCore/issues/10065#issuecomment-336495475

### 安装 

将[`Pomelo.EntityFrameworkCore.MySql`](https://www.nuget.org/packages/Pomelo.EntityFrameworkCore.MySql/) NuGet包安装到 ***.EntityFrameworkCore*** 项目。 

### 配置

#### 配置 DbContext 

把 `YourProjectNameDbContextConfigurer.cs` 用下面的代码段进行替换

```c#
public static class MySqlDemoDbContextConfigurer
{
    public static void Configure(DbContextOptionsBuilder<MySqlDemoDbContext> builder, string connectionString)
    {
        builder.UseMySql(connectionString);
    }

    public static void Configure(DbContextOptionsBuilder<MySqlDemoDbContext> builder, DbConnection connection)
    {
        builder.UseMySql(connection);
    }
 }
 ```

想要在ASP.NET Core和Entity Framework Core中使用MySQL一起使用需要做一些配置和变通。

#### 配置数据库连接字符串 

在 **.Web.Mvc/appsettings.json**将连接字符串更改为MySQL的连接字符串. 例如：

```js
{
  "ConnectionStrings": {
    "Default": "server=127.0.0.1;uid=root;pwd=1234;database=mysqldemodb"
  },
  ...
}

```

#### 解决方案

为了防止 EF Core 调用 `Program.BuildWebHost()`，我们需要重命名 `BuildWebHost`。例如，把他改成 `InitWebHost`。
若要了解需要重命名的原因, 请检查看以下 issues：

> **原因** : [EF Core 2.0: 设计时发生变更](https://github.com/aspnet/EntityFrameworkCore/issues/9033)
> 
> **解决方法** : [设计: 允许安装 IDesignTimeDbContextFactory 的 idesig-timedbcontext 模块](https://github.com/aspnet/EntityFrameworkCore/issues/9076#issuecomment-313278753)
>
> **注意 :** 如果不重命名 `BuildWebHost`，你将在运行时收到`BuildWebHost`方法执行错误。

### 创建数据库

删除  **\*.EntityFrameworkCore/Migrations** 文件夹。
因为 `Pomelo.EntityFrameworkCore.MySql` 将添加一些自己的配置文件以便使用Entity Framework Core。

开始构建数据库：

- 选择 **\*.Web.Mvc** 作为启动项。
- 打开 **包管理器控制台**, 然后选择 **.EntityFrameworkCore**。 
- 执行 `add-migration Initial_Migration` 命令。
- 执行 `update-database` 命令。

MySQL集成至此已经完成，你可以使用MySQL运行你的项目了。 

