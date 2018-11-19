### 下载起始项目
 
现在下载以 **ASP.NET Core** 和 **Entity Framework Core** 为模版的起始项目来实现集成SQLite：
[**ASP.NET Core 2.x** + **.NET Core Framework** + **Authentication** 的Multi-page template](https://aspnetboilerplate.com/Templates) 
我们将以此模版来展开本文的后续实现.

### 安装EntityFrameworkCore.Sqlite

安装 [`Microsoft.EntityFrameworkCore.Sqlite`](https://www.nuget.org/packages/Microsoft.EntityFrameworkCore.Sqlite/) NuGet到 **\*.EntityFrameworkCore** 项目中。

    >Install-Package Microsoft.EntityFrameworkCore.Sqlite

### 配置

首先需要在ASP.NET Core和Entity Framework Core中进行一些配置，从而使用SQLite。

#### 配置 DbContext  

由于SQLite并不支持多线程，因此需要在`SQLiteDemoEntityFrameworkModule.PreInitialize（）`方法中禁用事务。

> NOTE:在 [这里](https://github.com/XdX-Software/EasyDDD/issues/1) 可以查看有关此问题的更加详细的说明.

```c#
[DependsOn( typeof(SQLiteDemoCoreModule),  typeof(AbpZeroCoreEntityFrameworkCoreModule))]
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

在 `YourProjectNameDbContextConfigurer.cs` 中用以下代码进行替换：

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

#### 配置连接字符串

修改 ***.Web.Mvc/appsettings.json** 中的连接字符串，来实现连接到SQLite，如下: 

```js
{
  "ConnectionStrings": {
    "Default": "Data Source=SqliteDemoDb.db"
  },
  ...
}

```

#### 需要注意
 
为了防止EF Core调用`Program.BuildWebHost（）`重命名`BuildWebHost`。例如，将其更改为“InitWebHost”。
要了解为什么需要重命名，请检查以下问题，

> **原因** : [EF Core 2.0: design-time DbContext discovery changes](https://github.com/aspnet/EntityFrameworkCore/issues/9033)
> 
> **解决方法** : [Design: Allow IDesignTimeDbContextFactory to short-circuit service provider creation](https://github.com/aspnet/EntityFrameworkCore/issues/9076#issuecomment-313278753)
>
> **注意 :** 如果不重命名BuildWebHost，运行BuildWebHost方法时会出错.

### 创建数据库

在创建数据库之前，删除**\*.EntityFrameworkCore/Migrations** 文件夹下的所有迁移类。
`Microsoft.EntityFrameworkCore.Sqlite`将添加一些自己的配置来与Entity Framework Core一起使用。

我们现在已经准备好构建数据库了：
 
- 选择 **\*.Web.Mvc** 作为启动项目。
- 打开 **Package Manager Console**  并选择 **\*.EntityFrameworkCore** 项目。
- 运行 `add-migration Initial_Migration` 命令
- 运行 `update-database` 命令
 
The SQLite integration is now complete. You can now run your project with SQLite. 

SQLite集成现已完成。您现在可以使用SQLite运行项目。
