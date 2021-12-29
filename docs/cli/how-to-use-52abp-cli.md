# 如何使用52ABP-CLI命令行工具

**52abp-cli** 是52abp开发团队开发的一款cli工具，旨在让用户能更好的使用52abp框架创造价值。

可以通过命令行方式进行操作，快速创建业务模块。访问地址：https://www.nuget.org/packages/52abp-cli


> TIPS: 为了更好的使用 52abp-cli 工具，请先升级到最新使用 [L.52AbpPro.Identity.Core]() 模块的版本

## 52abp-cli的维护命令

### 安装

```shell
dotnet tool install -g 52abp-cli
```

### 升级

```shell
dotnet tool update -g 52abp-cli
```

### 卸载

```shell
dotnet tool uninstall -g 52abp-cli
```

### 开始使用

#### 查看帮助

```shell
52abp-cli --help
```

#### 创建业务模块

52abp-cli 可以快速创建一个包含 `.Web.Core` `.EntityFrameworkCore` `.Core` `.Application` 的业务模块，并将业务模块添加到主项目的 WebHost 中：

```shell
52abp-cli new  -s  sln文件全路径 -n 模块名称
```

##### 支持以下几种模块命名方式：
1. 创建一个名为 **MyBlog** 的模块到 **LTMCompanyName.YoyoCmsTemplate.sln** 项目中

   ```shell
   52abp-cli new m -s D:\dev\52abp\52ABP-Enterprise\src\yoyocmstemplate-aspnet-core\LTMCompanyName.YoyoCmsTemplate.sln -n MyBlog
   ```

2. 创建一个限定**项目名称**的模块到 **LTMCompanyName.YoyoCmsTemplate.sln** 项目中

   ```shell
   52abp-cli new m -s D:\dev\52abp\52ABP-Enterprise\src\yoyocmstemplate-aspnet-core\LTMCompanyName.YoyoCmsTemplate.sln -n ProjectName.MyBlog
   ```

3. 创建一个限定**公司名称**和**项目名称**的模块到 **LTMCompanyName.YoyoCmsTemplate.sln** 项目中

   ```shell
   52abp-cli new m -s D:\dev\52abp\52ABP-Enterprise\src\yoyocmstemplate-aspnet-core\LTMCompanyName.YoyoCmsTemplate.sln -n CompanyName.ProjectName.MyBlog
   ```


