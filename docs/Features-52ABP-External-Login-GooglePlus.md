# GooglePlus社交登陆应用配置

> 本文作者：52ABP开发团队 </br>
> 文章会随着版本进行更新，关注我们获取最新版本 </br>
> 本文出处：[https://www.52abp.com/wiki/52abp/latest](https://www.52abp.com/wiki/52abp/latest) </br>
> 源代码： https://www.github.com/52abp </br>

<!-- 简单的图文介绍: 关联代码位置 -->
配置流程:
---
- 访问[console.developers.google.com](https://console.developers.google.com/projectcreate?organizationId=0), 创建一个项目(Project):
  ![](images/2019-10-27-01-01-32.png)
  项目创建后结果如下:
  ![](images/2019-10-27-01-03-29.png)
- 项目创建完成后, 向项目中接入GooglePlus服务
    - 进入信息中心
    ![](images/2019-10-27-01-06-27.png)
    - 创建api服务
    ![](images/2019-10-27-01-07-09.png)
    - 在api服务中搜索`Google Plus`
    ![](images/2019-10-27-01-09-17.png)
    - 启用`Google Plus`服务
    ![](images/2019-10-27-01-10-26.png)
    - 启用服务后, 需要创建社交登陆所需的相关凭据
    ![](images/2019-10-27-01-17-34.png)
        - 在配置凭据之前, 需要先行配置授权页面信息
        ![](images/2019-10-27-01-18-18.png)
        ![](images/2019-10-27-01-23-34.png)
        - 再次回到凭据创建页面, 开始创建我们的OAuth凭据
        ![](images/2019-10-27-01-25-11.png)
        可以参考的配置如下:
        ![](images/2019-10-27-01-31-58.png)
    - 创建完成后跳转, 即可获取到我们所需要的client id和client secret, 复制填入配置文件即可
    ![](images/2019-10-27-01-33-44.png)
来文档中心了解更多：https://www.52abp.com/wiki/

### 微信关注我们不走丢

<img src="https://raw.githubusercontent.com/52ABP/Documents/V0.16/src/mvc/images/jiaoluowechat.png" class="img-fluid text-center " alt="公众号：角落的白板报" style="height: 80;width: 250px;"/>
