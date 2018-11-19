### 下载起始项目

Download a starter template with **ASP.NET Core** and **Entity Framework Core** to integrate SQLite. 
[Multi-page template with **ASP.NET Core 2.x** + **.NET Core Framework** + **Authentication**](https://aspnetboilerplate.com/Templates) 
will be explained in this document.

现在下载以 **ASP.NET Core** 和 **Entity Framework Core** 为模版的起始项目来实现集成SQLite. 
[Multi-page template with **ASP.NET Core 2.x** + **.NET Core Framework** + **Authentication**](https://aspnetboilerplate.com/Templates) 
我们将以此模版来展开本文的后续实现.

### Install 
### 安装EntityFrameworkCore.Sqlite

Install the [`Microsoft.EntityFrameworkCore.Sqlite`](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Sqlite/) NuGet package to the **\*.EntityFrameworkCore** project. 

安装 [`Microsoft.EntityFrameworkCore.Sqlite`](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Sqlite/) NuGet到 **\*.EntityFrameworkCore** 项目中。

    >Install-Package Microsoft.EntityFrameworkCore.Sqlite

### Configuration 
### 配置
Some configuration and workarounds are needed to use SQLite with ASP.NET Core and Entity Framework Core. 

在ASP.NET Core和Entity Framework Core中使用SQLite，首先需要进行一些配置。

#### Configure DbContext 
#### 配置 DbContext  

Since SQLite doesn't support multithreading, transactions should be disabled in the `SQLiteDemoEntityFrameworkModule.PreInitialize()` method.
由于SQLite并不支持多线程，因此需要在`SQLiteDemoEntityFrameworkModule.PreInitialize（）`方法中禁用事务。

> NOTE:在 [这里](https://github.com/XdX-Software/EasyDDD/issues/1) 可以查看有关此问题的更加详细的说明.

```c#
[DependsOn(
    typeof(SQLiteDemoCoreModule), 
    typeof(AbpZeroCoreEntityFrameworkCoreModule))]
public class SQLiteDemoEntityFrameworkModule : AbpModule
{
    public override void PreInitialize()
    {
        ...
        // add this line to disable transactions
        Configuration.UnitOfWork.IsTransactional = false;
        ...
    }
}
```

Replace `YourProjectNameDbContextConfigurer.cs` with the following lines

```c#
public static class SqliteDemoDbContextConfigurer
{
    public static void Configure(DbContextOptionsBuilder<SqliteDemoDbContext> builder, string connectionString)
    {
        builder.UseSqlite(connectionString);
    }

    public static void Configure(DbContextOptionsBuilder<SqliteDemoDbContext> builder, DbConnection connection)
    {
        builder.UseSqlite(connection);
    }
 }
 ```

#### Configure connection string 
#### 配置连接字符串

Change the connection string to your SQLite connection in ***.Web.Mvc/appsettings.json**. Example:
修改***.Web.Mvc/appsettings.json**.中的连接字符串，来实现连接到SQLite，如下:

```js
{
  "ConnectionStrings": {
    "Default": "Data Source=SqliteDemoDb.db"
  },
  ...
}

```

#### 一种解决方法

To prevent EF Core from calling `Program.BuildWebHost()` rename `BuildWebHost`. For example, change it to `InitWebHost`. 
To understand why it needs to be renamed check the following issues,

为了防止EF Core调用`Program.BuildWebHost（）`重命名`BuildWebHost`。例如，将其更改为“InitWebHost”。
要了解为什么需要重命名，请检查以下问题，

> **原因** : [EF Core 2.0: design-time DbContext discovery changes](https://github.com/aspnet/EntityFrameworkCore/issues/9033)
> 
> **解决方法** : [Design: Allow IDesignTimeDbContextFactory to short-circuit service provider creation](https://github.com/aspnet/EntityFrameworkCore/issues/9076#issuecomment-313278753)
>
> **注意 :** 如果不重命名BuildWebHost，运行BuildWebHost方法时会出错.

###创建数据库

Remove all migration classes under **\*.EntityFrameworkCore/Migrations** folder before creating database.
`Microsoft.EntityFrameworkCore.Sqlite` will add some of its own configuration to work with Entity Framework Core.
在创建数据库之前，删除**\*.EntityFrameworkCore/Migrations** 文件夹下的所有迁移类。
`Microsoft.EntityFrameworkCore.Sqlite`将添加一些自己的配置来与Entity Framework Core一起使用。


Now it's ready to build the database.
现在已经准备好构建数据库了。

- Select **\*.Web.Mvc** as the startup project.
- Open **Package Manager Console** and select the **\*.EntityFrameworkCore** project.
- Run the `add-migration Initial_Migration` command
- Run the `update-database` command

- 选择 **\*.Web.Mvc** 作为启动项目。
- 打开 **Package Manager Console**  并选择 **\*.EntityFrameworkCore** 项目。
- 运行 `add-migration Initial_Migration` 命令
- 运行 `update-database` 命令
 
The SQLite integration is now complete. You can now run your project with SQLite. 
SQLite集成现已完成。您现在可以使用SQLite运行项目。
