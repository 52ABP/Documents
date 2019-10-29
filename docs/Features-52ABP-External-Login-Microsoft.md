# 微软社交登陆应用配置

> 本文作者：52ABP开发团队 </br>
> 文章会随着版本进行更新，关注我们获取最新版本 </br>
> 本文出处：[https://www.52abp.com/wiki/52abp/latest](https://www.52abp.com/wiki/52abp/latest) </br>
> 源代码： https://www.github.com/52abp </br>

<!-- 简单的图文介绍: 关联代码位置 -->
配置流程:
---
- 访问[Azure.com](https://portal.azure.com/#blade/Microsoft_AAD_RegisteredApps/ApplicationsListBlade), 创建一个应用程序注册(App Registration):
  ![](images/../licecap.gif)
- 填入相关必填项, 创建应用
  ![](images/2019-10-24-00-05-51.png)
  应用创建后结果如下, 可以在此结果页获取到我们所需要的client id
  ![](images/2019-10-24-00-50-23.png)
- 应用创建完成后, 进行应用的后续配置
    - 应用基本信息配置
    ![](images/2019-10-24-00-44-41.png)
    - 应用授权回调相关配置
    ![](images/2019-10-24-00-16-50.png)
    - 生成client secret
    ![](images/2019-10-24-00-48-03.png)
来文档中心了解更多：https://www.52abp.com/wiki/

### 微信关注我们不走丢

<img src="https://raw.githubusercontent.com/52ABP/Documents/V0.16/src/mvc/images/jiaoluowechat.png" class="img-fluid text-center " alt="公众号：角落的白板报" style="height: 80;width: 250px;"/>
