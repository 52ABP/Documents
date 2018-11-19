### 介绍

虽然我们的模板默认使用的是SQL Server，但你也可以轻松修改它们来使用MySql。

按照以下步骤操作，可以把数据库切换到MySql。

#### 下载项目

Go to <http://aspnetboilerplate.com/Templates> and download a new
project. Select ASP.NET MVC 5.x tab and don't forget to select Entity
Framework.
打开链接：http://aspnetboilerplate.com/Templates 并下载一个新项目。选择ASP.NET MVC 5.x选项，选择EntityFramework实体框架。

#### 安装 MySql.Data.Entity

You then need to install the
[MySql.Data.Entity](https://www.nuget.org/packages/MySql.Data.Entity/)
NuGet package into your **.EntityFramework** and **.Web** projects.
Installing this NuGet package into your **.Web** project should make the
necessary changes in your web.config file.

然后，您需要将MySql.Data.Entity NuGet包安装到.EntityFramework和.Web项目中。
把NuGet包安装到.Web项目中后，会更新web.config文件。

Open your DbContext's configuration class (Configuration.cs) and place
the following code in it's constructor
打开DbContext的配置类（Configuration.cs）并将以下代码放在它的构造函数中。

    SetSqlGenerator("MySql.Data.MySqlClient", new MySql.Data.Entity.MySqlMigrationSqlGenerator()); 


#### 配置ConnectionString

You need to change your connection string in the web.config file in
order to work with your MySql database. An example connection string
would be:
您需要更改web.config文件中的连接字符串才能使用MySql数据库。示例连接字符串如下：

    <add name="Default" connectionString="server=localhost;port=3306;database=sampledb;uid=root;password=***" providerName="MySql.Data.MySqlClient"/>

#### 重新生成迁移

If you choose "Include login, register, user, role and tenant management pages" while downloading your startup
template, there will be some migration files included in your project.
These files are generated for Sql Server. Delete all the migration files
in your **.EntityFramework** project under the Migrations folder. Migration
files start with a timestamp. A migration file name should look like this
"201506210746108\_AbpZero\_Initial"

如果在下载启动模板时选择“包括登录，注册，用户，角色和租户管理页面”，则项目中将包含一些迁移文件。这些文件是为Sql Server生成的。
删除迁移文件夹下的.EntityFramework项目中的所有迁移文件。迁移文件以时间戳开头。
迁移文件名应如下所示“201506210746108_AbpZero_Initial”

After deleting all the migration files, select your **.Web** project as the
startup project, open Visual Studio's Package Manager Console and select
the **.EntityFramework** project as the default project in the Package Manager
Console. Then run the following command to add a migration for MySql.

删除所有迁移文件后，选择.Web项目作为启动项目，打开Visual Studio的程序包管理器控制台，并选择.EntityFramework项目作为程序包管理器控制台中的默认项目。然后运行以下命令为MySql添加迁移。

    Add-Migration "AbpZero_Initial"

Now you can create your database using the following command
现在，您可以使用以下命令创建数据库

    Update-Database

That's it! You can now run your project with MySql.
而已！您现在可以使用MySql运行项目。
