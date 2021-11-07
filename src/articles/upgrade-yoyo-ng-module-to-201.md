## 前言

本篇内容为指导从 `yoyo-ng-module 1.x` 升级到 `yoyo-ng-module 2.x`

## 详细说明

52ABP 前端框架采用的是 基于 NG-Zorro 构建的脚手架 NG-Alian，将其修改并整合到前端模块`yoyo-ng-module`中

最初支持版本: `Angular6 + NG-Zorro(低于1.8)版本 + NG-Alian 1.x`

近期由于 NG-Zorro 1.8 版本的升级对原有图标的升级是破坏式的，并且 NG-Alian 也发布了 2.0 正式版，于是乎近几日也对`yoyo-ng-module`进行了升级，发布了 2.0.1。

升级部分:

- 整合 NG-Alian 2.0 与 ABP 前端模块
- 支持 NG-Zorro 1.8
- 菜单布局优化

新版本可以通过 [官网](https://www.52abp.com/download) 或者 [github](https://github.com/52ABP/LTMCompanyNameFree.YoyoCmsTemplate) 直接下载。

**升级教程正式开始**

# 1、升级 ng-zorro、yoyo-ng-module

_以下命令看个人喜好使用_

- 安装 ng-zorro1.8
  ```
  npm命令 :  npm install ng-zorro-antd@1.8.0
  yarn命令:  yarn add ng-zorro-antd@1.8.0
  ```
- 安装 yoyo-ng-module 2.0.1
  ```
  npm命令 :  npm install yoyo-ng-module@2.0.1
  yarn命令:  yarn add yoyo-ng-module@2.0.1
  ```
- 修复 ng-zorro 图标丢失（官方文档链接：[点击这里](https://ng.ant.design/components/icon/zh)）
  ```
  ng g ng-zorro-antd:fix-icon
  ```

# 2、新增/替换 前端项目文件

从 [官网](https://www.52abp.com/download) 或者 [github](https://github.com/52ABP/LTMCompanyNameFree.YoyoCmsTemplate) 下载 **4.0.0** 的代码，将这里面的部分内容替换到原有项目中

**注意 :** 替换文件时请确认是否有自定义功能已添加,替换前请注意备份

### account

- `替换 文件` src/account/account.module.ts
- `替换 文件` src/account/login/login.component.html
- `替换 文件` src/account/login/login.component.less
- `替换 文件` src/account/register/register.component.html
- `替换 文件` src/account/tenant/tenant-change-modal.component.html
- `替换 文件` src/account/tenant-register/tenant-register.component.html

### app

- `替换 文件` src/app/app.component.html
- `替换 文件` src/app/app.component.ts
- `参照修改 文件` src/app/AppMenus.ts
- `替换 文件` src/app/home/home.component.html
- `替换 文件夹(目录)` src/app/layout

### styles

- `替换 文件` src/styles.less
- `替换 文件` src/styles/index.less
- `替换 文件` src/styles/theme.less
- `新增 文件` src/styles/theme-variable.less
- `新增 文件` src/style-icons-auto.ts
- `新增 文件` src/style-icons.ts

### shared

- `替换 文件` src/shared/shared.module.ts

### assets

- `替换 文件` src/assets/appconfig.dev.json
- `替换 文件` src/shared/appconfig.prod.json

### 其它

- `替换 文件` src/root.module.ts
- `替换 文件` src/root.component.ts
- `替换 文件` src/yoyo.module.ts
- `替换 文件` src/AppPreBootstrap.ts

---

以上步骤执行完成之后即可成功升级到 ng-zorro1.8.x + ng-alian 2.0

如有疑问或发生问题请加入 qq 群：**633751348**

**转载请注明原文链接和作者名称**
