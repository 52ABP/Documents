### 介绍

虽然我们的模板默认使用的是SQL Server，但你也可以轻松修改配置来使用MySql。

按照以下步骤操作，可以把数据库切换到MySql。

#### 下载项目

打开链接：http://aspnetboilerplate.com/Templates 并下载一个新项目。选择ASP.NET MVC 5.x项目并选择EntityFramework实体框架。

#### 安装 MySql.Data.Entity

然后，你需要把MySql.Data.Entity 的NuGet包安装到.EntityFramework和.Web项目中。把NuGet包安装到.Web项目中后，会自动更新web.config文件。

    SetSqlGenerator("MySql.Data.MySqlClient", new MySql.Data.Entity.MySqlMigrationSqlGenerator()); 


#### 更新数据库连接字符串ConnectionString

你需要更改web.config文件中的连接字符串才能使用MySql数据库。示例连接字符串如下：

    <add name="Default" connectionString="server=localhost;port=3306;database=sampledb;uid=root;password=***" providerName="MySql.Data.MySqlClient"/>

#### 重新生成迁移

如果在下载启动模板时选择“包括登录，注册，用户，角色和租户管理页面”，则项目中将包含一些迁移文件。这些文件是为Sql Server生成的。
删除迁移文件夹下的.EntityFramework项目中的所有迁移文件。迁移文件以时间戳开头。
迁移文件名应如下所示“201506210746108_AbpZero_Initial”。

删除所有迁移文件后，选择.Web项目作为启动项目，打开Visual Studio的程序包管理器控制台，并选择.EntityFramework项目作为程序包管理器控制台中的默认项目。然后运行以下命令为MySql添加迁移：

    Add-Migration "AbpZero_Initial"

现在，您可以使用以下命令创建并初始化数据库：

    Update-Database

完成！你现在可以使用MySql作为你项目的数据库了。
