
# How do you get started with the abp framework in 2019 !


[[_TOC_]]
 

# 2019年起如何开始学习ABP框架系列文章-开篇有益

本文的目的是为了让刚刚接触ABP框架的同学或者准备接触ABP框架的同学，能够理解和搞明白ABP框架到底是怎么回事，毕竟它发展了好几年的时间。社区中有很多人做 了ABP的资料和文章包括我自己也建立了52ABP，社区中还有ABPplus等等的内容。对于很多不了解ABP框架的人，会产生无限的疑惑和不知道如何下手的痛苦。

包括ABP框架官方自己也有很多个版本。我作为从15年开始推广ABP框架的人之一，认为有必要将各个版本的ABP框架做出说明。以及导航为大家学习ABP框架更加详细的资料。【本文的原文发布在github：[如何在2019年开始使用abp框架?](https://github.com/52ABP/Home/blob/master/Articles/HowToGetStartedwiththeabpframeworkin2019/Introduction.md)，欢迎参与协同哦~】

# 序

2019年起该如何学习ABP框架。我想这是很多刚刚接触ABP框架人的疑惑。ABP缘起于github ，在国内发扬于博客园。目前ABP已经在各种项目中进行过了落地和实践，保证了他能够良好的为企业级开发应用做好服务。所以越来越多的小伙伴开始尝试ABP框架，但是遇到了各种难题，故这篇文章是为了帮助大家建立正确的ABP框架的认识篇内容。


## 为什么要学习使用ABP框架呢？
 我想这个是很多同学的疑问，有那么多的框架可以选择，我为什么选择你呢。
在 [叶伟民的博客](https://www.cnblogs.com/adalovelacer/p/abp-quickly-delivery-3-why-use-ABP.html)中 从站在商业视角的阐述了为什么使用代码生成器，因为快。为项目节约时间。 时间就是金钱, 效率就是生命。
从我个人的角度上来说，
认为第一是为了进行技术投资，

第二是为了看看你自己在技术这条路上的瓶颈，


第三学了它基本可以涨工资。

>ABP官方的介绍是：ASP.NET  Boilerplate是一个用最佳实践和流行技术开发现代WEB应用程序的新起点，它旨在成为一个通用的WEB应用程序基础框架和项目模板。基于DDD的经典分层架构思想，实现了众多DDD的概念（但没有实现所有DDD的概念）。

我认为很多人看到这些话就觉得牛逼吹的有点大了。但是其实不大，因为这款框架真的足够有这么的优秀。

- 从技术投资层面，你可以学习到新的思维模式和了解.net core 和目前世界上最流行的技术体系和架构，他们有不少的内容都在ABP中进行了落地。
- 从看看自己瓶颈的角度上，目前ABP已经是一个较为完整的生态，我们在国内看到一些公司招聘的时候，已经有提到有了解或者ABP框架的优先，说明了ABP在国内已经有很多公司在进行使用了。而学会使用ABP框架后，你会忍不住的去用前端的东西，很容易把自己培养为全栈开发，在前端配合Angular开发，基本上没有太多的难度。
- 涨工资就是一个很好玩的话题了，因为ABP框架的门槛比较高，后面我会写一个劝退指南，你如果这些都不掌握，很难把ABP框架使用的好，但是要是把劝退指南中的知识点都学会了。涨工资是个很轻松简单的事情了。因为你会发现面试官问你的各种问题和很多业务的处理场景，ABP框架中已经有实现了，对于我们而言只要去把ABP搞明白，很多技术点的难题，反而不是特别大的问题了。


# ABP简单介绍
目前ABP有很多的内容，很多同学听到版本就是懵逼脸，一会儿是 abp ，abp zero，module zero，abp vnext 这些内容。
我做一个解释性的说明 吧。造成这些问题的原因是因为历史。
## 历史性问题

ABP项目最早是13年的时候，那时候没有.Net Core和ASP.NET Core,也没有Angular2 + 所以ABP最早的时候，是从.Netframework 开始做的开发，现在大家都知道了。.NET CORE官方版本都已经发布到2.2了。那么在这样的历史下 ABP本身也出了很多版本。
ABP是“ASP.NET Boilerplate Project (ASP.NET样板项目)”的简称。
ASP.NET Boilerplate是一个用最佳实践和流行技术开发现代WEB应用程序的新起点，它旨在成为一个通用的WEB应用程序基础框架和项目模板。
ASP.NET Boilerplate 基于DDD的经典分层架构思想，实现了众多DDD的概念（但没有实现所有DDD的概念）。
* ABP的官方网站：http://www.aspnetboilerplate.com
* ABP在Github上的开源项目：https://github.com/aspnetboilerplate
* 52ABP的官方网站：https://www.52abp.com
* 52ABP在Github上的开源项目：https://github.com/52abp

上面是很多地方都会介绍的，在整个ABP中文文档中也会涉及：https://www.52abp.com/Wiki/abp-cn/latest/1.1ABP%E6%80%BB%E4%BD%93%E4%BB%8B%E7%BB%8D-%E5%85%A5%E9%97%A8%E4%BB%8B%E7%BB%8D

## ABP框架各个版本介绍

关于ABP那么的版本和听不明白词汇的答疑，ABP、Zero、ABPZero和ABPVnext的区别，这个是为新人做介绍的时候说明。

| 名称 | 别名 | 官方地址 | 仓库 | 中文文档地址 | 官方文档 |说明 | 
| :--- | :--: | :------: | :--: | :--: | :------: | :------: |
| ABP | abp | [网址](https://aspnetboilerplate.com/Pages/Documents) | [github](https://github.com/aspnetboilerplate/aspnetboilerplate) | [中文文档](https://www.52abp.com/Wiki/abp-cn/latest/1.1ABP%E6%80%BB%E4%BD%93%E4%BB%8B%E7%BB%8D-%E5%85%A5%E9%97%A8%E4%BB%8B%E7%BB%8D) | [英文文档](https://aspnetboilerplate.com/Pages/Documents) |社区中提到的文档和说明中最多的说到 ABP 都是指它，也是很多社区基于它做的很多功能和扩展 | 
| Module Zero|zero | [网址](https://aspnetboilerplate.com/Pages/Documents) | [github](https://github.com/aspnetboilerplate/aspnetboilerplate) | [中文文档](https://www.52abp.com/Wiki/abp-cn/latest/1.1ABP%E6%80%BB%E4%BD%93%E4%BB%8B%E7%BB%8D-%E5%85%A5%E9%97%A8%E4%BB%8B%E7%BB%8D) | [英文文档](https://aspnetboilerplate.com/Pages/Documents) |在ABP3.0的版本中官方将modulezero合并到了主仓库，对于2.0以下的版本，可以到[仓库](https://github.com/aspnetboilerplate/module-core-forsaken)中查看| 
| ASP.NETZERO |abpzero, abp企业版, abp收费版| [网址](https://aspnetzero.com/) | [github](https://github.com/aspnetzero/) |  [文档](https://www.52abp.com/Wiki/abpzero/latest/Index) | [英文文档](https://docs.aspnetzero.com/documents/zero/latest/Index) |这是ABP官方提供的收费版本，里面的版本也包含了很多的内容 Angular、.net core等的内容,目前也是在国内环境中各种被破解的版本 |
| ABPVNext |abp.io abp新版| [网址](https://abp.io/) [中文网址](https://cn.abp.io) | [github](https://github.com/aspnetzero/) |  [中文文档](https://www.52abp.com/Wiki/abpvnext-cn/latest/Index) [中文文档2](https://cn.abp.io/documents/abp/latest/Index) | [英文文档](https://www.52abp.com/Wiki/abpvnext-/latest/Index)[英文文档2](https://abp.io/documents/abp/latest/Index) |这是为了抛弃掉.net framework版本下的包袱，重新启动的abp框架，目的是为了放弃对传统技术的支持，让asp.net core能够自身做到更加的模块化 |

 以上的所有中文英文的文档都可以从[https://www.52abp.com/](https://www.52abp.com/Wiki)中获取到也欢迎大家进行协同更新



# 52ABP和ABP框架的关系

最近这半年我自己搭建了一套52ABP框架也建立了 `https://www.52abp.com`的网站，很多人也懵逼,大多数人的疑问如下：
- 52ABP框架是啥？
- 和ABP是啥什么关系。
- 你的这个会和ABP冲突吗？
- 为什么你要自己做一个这个版本出来？

我作为统一的回答吧，52ABP是基于ABP之上开发的一套框架，他不扎根于基础设施，他更多做的事情是让大家在开发功能的时候更加的方便。
所以他不会和ABP框架冲突，甚至我建议大家可以直接使用52ABP框架进行开发，因为52ABP有一整套的开发设施，项目模板生成器，代码生成器、文档、视频等内容。可以节约大家的时间和精力。

## 关于52ABP更加详细的说明。https://github.com/52ABP/Home 我们已经在这里阐述了。



# 快速上手
快速启动abp的话，博客园中有很多，我就快速的将有关的文字贴出来。
 




52ABP和ABP官网都可以作为快速入手的路径。

https://www.52abp.com/

http://www.aspnetboilerplate.com

# 文档



# 版本的区别及关键词解释

# ABP框架劝退篇

初级程序员应该去补充的资料


# 项目

# 代码生成器

# 收费和免费

# 资料推荐
https://www.cnblogs.com/adalovelacer/p/abp-quickly-delivery-1-catalog.html
https://www.cnblogs.com/adalovelacer/p/speciallist-of-guang-zhou-dot-net-club.html
https://personball.com/


 
