# 账号密码登录

> 本文作者：52ABP开发团队 </br>
> 文档会随着版本进行更新，关注[52ABP.com](https://www.52abp.com)获取最新版本 </br>
> 本文出处：[https://www.52abp.com/wiki/52abp/latest/](https://www.52abp.com/wiki/52abp/latest/) </br>
> 源码下载： [https://code.52abp.com/52abp](https://code.52abp.com/52abp) </br>

<!-- 简单的图文介绍: 关联代码位置 -->
后台API：
---
所在位置：`LTMCompanyName.YoyoCmsTemplate.Controllers.TokenAuthController.Authenticate`

![后台API](images/Features-52ABP-NG-Login-3.png)

前端实现：
---
所在位置：`src/account/login/login.service.ts/authenticate`，使用时，需注入`LoginService`
![前端实现](images/Features-52ABP-NG-Login-5.png)
![注入LoginService](images/Features-52ABP-NG-Login-6.png)


<!-- 简单的图文介绍: 效果展示 -->
登陆页
---
![登陆页](images/Features-52ABP-NG-Login-1.png)


登录时，可选择**租户**（**留空**则切换到**宿主**）
---
![切换租户](images/Features-52ABP-NG-Login-4.png)
![选择租户](images/Features-52ABP-NG-Login-2.png)

<!-- 详细的图文介绍: 常见的应用场景&可能的注意事项 -->
登录失败超过限制后，会锁定用户账户（**相关参数**可在后台设置）


来文档中心了解更多：https://www.52abp.com/wiki/

## 微信扫码关注我们

<img src="https://www.52abp.com/imgs/money-QR/jiaoluo_wechat_QR.jpg" class="img-fluid text-center " alt="公众号：角落的白板报" style="height: 80;width: 250px;"/>
