### 下载起始模板

下载带有 **ASP.NET Core** 和 **Entity Framework Core** 的起始模板， 以集成 PostgreSQL。 本文档将介绍[集成**ASP.NET Core 2.x+** 和 **Entity Framework Core** + 身份验证的多页模板](https://aspnetboilerplate.com/Templates)。

### 安装

将[`Npgsql.EntityFrameworkCore.PostgreSQL`](https://www.nuget.org/packages/Npgsql.EntityFrameworkCore.PostgreSQL/)NuGet包安装到 **.EntityFrameworkCore**项目文件中。

### 配置

在ASP.NET Core 和 Entity Framework Core中使用 PostgreSQL 需要做一些配置和变通。

#### 配置 Dbcontext 

使用以下代码段替换 `YourProjectNameDbContextConfigurer.cs`

```c#
public static class PostgreSqlDemoDbContextConfigurer
{
    public static void Configure(DbContextOptionsBuilder<PostgreSqlDemoDbContext> builder, string connectionString)
    {
        builder.UseNpgsql(connectionString);
    }

    public static void Configure(DbContextOptionsBuilder<PostgreSqlDemoDbContext> builder, DbConnection connection)
    {
        builder.UseNpgsql(connection);
    }
 }
```

#### 配置数据库连接字符串 

在 **.Web.Mvc/appsettings.json** 配置文件中将连接字符串更改为你的 PostgreSQL 的连接字符串，例如：

```js
{
  "ConnectionStrings": {
    "Default": "User ID=postgres;Password=123;Host=localhost;Port=5432;Database=PostgreSqlDemoDb;Pooling=true;"
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

在创建数据库之前，应该向 DbContext中添加以下代码段来更改应用程序语言文本的 "value" 属性的最大长度，因为 MS SQL 和 PostgreSQL 中字符的最大长度是不同的。

```c#
public class PostgreSqlDemoDbContext : AbpZeroDbContext<Tenant, Role, User, PostgreSqlDemoDbContext>
{
    public PostgreSqlDemoDbContext(DbContextOptions<PostgreSqlDemoDbContext> options)
        : base(options)
    {
    }

    // add these lines to override max length of property
    // we should set max length smaller than the PostgreSQL allowed size (10485760)
    protected override void OnModelCreating(ModelBuilder modelBuilder)
    {
    	base.OnModelCreating(modelBuilder);
    	
        modelBuilder.Entity<ApplicationLanguageText>()
            .Property(p => p.Value)
            .HasMaxLength(100); // any integer that is smaller than 10485760
    }
}
```

删除 **.EntityFrameworkCore/Migrations** 文件夹，因为 `Npgsql.EntityFrameworkCore.PostgreSQL`将添加一些自己的配置文件以便使用Entity Framework Core。

开始构建数据库：

- 选择 **\*.Web.Mvc** 作为启动项。
- 打开包管理器控制台, 然后选择 **.EntityFrameworkCore**。 
- 执行 `add-migration Initial_Migration` 命令。
- 执行 `update-database` 命令。

PostgreSQL 集成至此已经全部完成，你可以使用PostgreSQL运行你的项目了。
