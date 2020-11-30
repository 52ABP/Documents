# 更新日志

> 文档会随着版本进行更新，关注[52ABP.com](https://www.52abp.com)获取最新版本 </br>
> 本文出处：[https://www.52abp.com/wiki/52abp/latest/](https://www.52abp.com/wiki/52abp/latest/) </br>
> 源代码： https://code.52abp.com/52abp </br>


本文介绍的52ABP-PRO的更新日志记录的摘要。
详细的发布说明在企业仓库中共享，（仅供客户使用）。

## V3.7.0 (2020年11月24日)

- 补充完整的Docker-compose的文件
- 多租户可通过配置文件进行启动
- 在线课程，章节页面可以进行折叠。
- 扩展appsettings配置内容 [757a66](https://code.52abp.com/52abp/pro/52ABP-Enterprise/-/merge_requests/85/diffs?commit_id=757a66e60b7eea89dc587bbe701e855613fa1bff)
- 修复批量删除用户的bug
- 增强后端添加用户的激活逻辑
- angular端引入qq自定义登录
- 补充markdown的剪贴板粘贴事件
- 优化审计日志的查询性能
- 更新博客模块内容
- 引入sample-table前端表格内容
- 配置文件增加数据库驱动类型和驱动证书选项[a9b4a438ce211160202634e3a35f8aff5e1d9a8c](https://code.52abp.com/52abp/pro/52ABP-Enterprise/-/merge_requests/85/diffs?commit_id=a9b4a438ce211160202634e3a35f8aff5e1d9a8c)
- 增加c-simplemde用于粘贴上传图片
- 增加用户头像组件/修改用户页面
- 更新博客 列表 详情，增加tag标记查询

## V3.6.1 (2020年8月27日)

* 升级ABP版本到5.12
* 统一处理L52ABP版本号

## V3.6.0 (2020年8月17日)

*  升级angular到9
*  升级ABP到5.9版本
* 新增博客模块
* 新增mooc模块
* 修复vue版本的相应异常
* MVC版本依然不推荐使用



## V3.2.0  更新内容(2020年3月19日)

### 新增功能

*  增加健康检查模块
*  增加文件管理模块
*  增加博客模块
*  增加时间选择器
*  新增一个登陆页面

### 优化内容
*  开启MARS，提升DbContext连接
*  引入editorconfig文件以及优化部分文件的格式化。
*  优化Excel内容。
*  处理一些Angular9中将要废弃的方法或者服务。
 


## V3.1.0 更新内容(2020年2月19日)


- 支持集成.NET Core 3.1.1
- 支持 Angular 8.2.3
- 支付宝支付Demo
- 用户批量导入
- 地址选择
- 日期时间空间
- Markdown编辑器
- 富文本编辑器
- 增加 用户管理的单元测试
- 增加角色管理的单元测试
- 增加组织单元管理的单元测试
- 增加多语言管理的单元测试
- 添加监控页面
- 修复了API中枚举无法转换为string类型的问题
- 代码生成器-增加自动导出默认功能
- 修复Angular的Dockerfile包文件
- 时间选择器集成Moment.js
- 修复Excel模板接口暴露问题
- 修复已知的Bug  
### 适配最新版代码生成器


- 配套代码生成器,提升易用性前后端模板
- 生成的代码遵循DDD（领域驱动设计）的规范
- 自动生成单元测试
- 生成导出Excel功能
- 增强前端控件 
 
 

## V2.5.0(2019年11月8日 )

- 修复调度管理功能，默认注入的问题
- 添加演示Demo模块。
- 集成markdown编辑器
- 增加用户导出功能
- 组织单元功能增加添加角色绑定
- 添加第三方登录模块。
  - 支持QQ
  - 支持Microsoft
  - 支持Facebook
  - 支持微信
  - 支持Google
- Vue 前端项目基础模块搭建完毕

## V2.0.0（2019年6月15日）

- 本地化功能增强，替换Xml为Json文件
- 增强Hangfire，补充Angular版的Hangfire模块组件
- 增加实时通知功能，增加signalr
- 升级ABP版本到4.5.0
- 增加SignalR通知添加，默认为关闭状态
- 集成通知框功能
- 增加邮箱发送功能，启用MailKit
- 增加Excel导出基类
- 增加ABPSession 扩展基类
  
  等待补充


## V1.3.0(2019年5月22日)


- 升级Swashbuckle.AspNetCore.SwaggerUI 版本到4.0 
- 默认增加WebAPI，生成SwaggerUI的中文注释内容 
- SwaggerUI的内容增强
- 替换谷歌CDN字体节点 


## V1.2.0（2019 年 1 月 9 日）

- 升级模板框架基础信息内容
- 升级.NET CORE 到 2.2.1
- 升级 ABP 版本到 4.0.2
- 升级 EF Core 到 2.2
- 修改 Readme 文件，让其更加易读
- 处理模板中的部分 bug 内容 
- 前端移除 yoyo-ng-module 模块
- 前端引入 ng-alian、@delon 模块
- 前端修改项目结构
 

- ABP 版本升级为 4.0.2
- 前端支持 ng-zorro 1.8
- 前端 yoyo-ng-module 升级到 2.0.1
- 旧版本升级到新版本指南[升级指南](https://www.52abp.com/BlogDetails/7)


来文档中心了解更多：https://www.52abp.com/wiki/ 

## 微信扫码关注我们

<div class="text-center ">
 <img src="https://www.52abp.com/imgs/money-QR/jiaoluo_wechat_QR.jpg" class="img-fluid text-center " alt="公众号：角落的白板报" style="
    height: 80;
    width: 250px;"/>
</div>
