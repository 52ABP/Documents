> 阅读文本大概需要 8 分钟。

标题使用的是**进化**这个词语，是因为 .NET 在不断的努力，也在不断的重构。
这篇文章的更多目的和意义在于科普，俗称“传教”。
 


 # 持续进化的 .NET
![image.png](https://upload-images.jianshu.io/upload_images/1979022-801fe113610c2aaa.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)




这张图即是一个学习的路线图同样他也是 .NET 平台的进化图。也是代表着 未来.NET 的发展方向。
今天的故事呢，就会根据上图中的名词一个个的解释下来。让各位更好的了解.NET 。

  # .NET到底是什么？

  在过去的日子中大家提到 .NET 通常是指 .NET Framework 这么一个框架。但是随着.NET技术的发展，时至今日，广义的 .NET指包含 **.NET Framework**，**.NET Core**，**Mono**在内，是基于.NET技术的整个产品系列。



> .NET 是一个通用开发平台。 它具有几项关键功能，例如支持多种编程语言、异步和并发编程模型以及本机互操作性，可以支持跨多个平台的各种方案。
 .NET 开发可以实现包括 .NET Framework、.NET Core 和 Mono。 .NET 的所有实现都有一个名为 .NET Standard 的通用 API 规范。
.NET 拥有惊人的性能和开发效率，并且拥有数百万的开发者。

以上就是最新的.NET的介绍。以后提到.NET 不再仅仅是.NET Framework 了。


我也就微软着新生的 .NET 或者说进化后的.NET来说说过往吧。

# .NET Framework
> 传统的 .NET Framework是以一种采用系统虚拟机运行的编程平台，以(通用语言运行库)CLR（Common Language Runtime）为基础，支持多种语言（C#、F#、VB .NET、C++、Python等）的开发。

这也是我们目前市面上用到最多也是大家最熟悉的.NET，它是目前在市场中的占比是最大的，他很成熟也很稳定，但是他的弱点是在于他天生不具备跨平台，这也是被广大程序员所诟病的，他需要跨平台，是需要通过配合Mono来使用，它更多的运行在Windows服务器上，需要IIS作为宿主。

而提到.NET Framework就不得不提到Java了。
# .NET Framework VS Java

 甲骨文(Oracle)公司的Java语言和J2ee技术是.NET平台的竞争对手之一。

说起.NET的起源，还得先说到Java。众所周知，Java是一个主打敏捷开发，跨平台的编程语言。而.NET的诞生，与Java有着千丝万缕的联系。

> Java的历史可以追溯到20世纪90年代，最初是由Sun公司为了实现电子产品智能化而开发的程序语言，主打的设计思想是敏捷开发和跨平台。1995年Java正式推出之后，立刻受到了包括IBM、Apple、Adobe、HP和微软在内的各大公司的追捧。随后几年Java的发展势如破竹，作为一款收费产品，Java给Sun公司带来了非常可观的盈利（Java已于2006年底宣布免费开源）。而微软作为软件大厂，当然不愿看着Java一家独大，同时也意识到了敏捷开发的巨大前景，由此诞生了Microsoft .NET。

> .NET框架作为Visual Studio的组件之一发放，自2002年全新VS .NET搭载.NET 1.0起，.NET至今已更新四个主版本，.NET 4.0于2010年随VS2010发布， 目前最新的 .NET Framework 版本为4.7.1。来源 

> .NET与Java有非常多的相似之处，二者都是即时编译（JIT）的动态语言。这类语言中，项目编译生成的目标文件并不是机器码，而是需要由运行时环境进行即时编译的特殊代码。在Java中这种特殊代码叫做字节码（bytecode），而.NET中则叫做中间语言（Common Intermediate Language，简称IL）。Java官方的运行时环境叫做JRE（Java Runtime Environment），而.NET官方的运行时环境叫做CLR（Common Language Runtime）。


**而我要吐槽的地方就在这里 ** 经常有很多人唱衰.NET 说BAT都不用 .NET 都是用java的。

 # 为什么国内的互联网公司都使用的是JAVA呢？


拨开迷雾看本质。
- 阿里巴巴 1999年成立 
- 百度2000年成立  
- 腾讯 1998年成立 。
> .NET 2002年才发布1.0版本。。你告诉我 他们有的选吗？

### 有人要提出京东 是从.NET 转的java ?

为什么，因为那个时候 .NET 不开源没有现成的大型电商、分布式、集群的解决方案，而java有大把的电商和互联网人才，注定了会选择JAVA而不是 .NET 。
**或许还有就是舍不得钱啊，毕竟 windows 服务器的授权费贵。** ~皮一下很开心。
所以 .NET 错在于它出生的晚了，不支持跨平台。 中国的互联网公司一开始就没有什么选择。 


 # .NET的跨平台之路
在和Java 的博弈和对战中，我们都知道 .NET Framework一直被吊打，尤其在国内。好在 2014年11月12日，微软宣布将完全开放.NET框架的源代码，并提供给Linux和OS X使用。[[来源]](https://weblogs.asp.net/scottgu/announcing-open-source-of-net-core-framework-net-core-distribution-for-linux-osx-and-free-visual-studio-community-edition)

听了这么一则新闻之后大家知道 .NET或许还有机会打一波翻身仗。但是早在这个新闻之前其实就有Mono这么一个 .NET 跨平台解决方案。

# Mono 神奇的跨平台解决方案


所以如果有人问你，.NET Framework 怎么跨平台，告诉他，可以使用Mono。
那 Mono 到底是什么？
它为什么可以跨平台？

在 .NET 开源之前，需要首先了解 Mono，了解 Mono [[维基Mono]](http://www.wikipedia.org/wiki/Mono) 

考虑到大多人咳咳不方便搭梯子以及英文不是很好,我摘录和转载了几个博主的文章。
 
> .NET Framework是由微软独立开发，闭源且具有专利性质的独家技术，并且微软只提供了针对Windows系统的支持。而作为同类竞争对手的Java，却能通杀包括x86、ARM在内的主流硬件平台，软件方面也支持包括Windows、Linux、Android在内的各种桌面、移动、嵌入式系统。

> Mono 是一个由 Xamarin 公司（先前是 Novell，最早为 Ximian）所主持的自由开放源代码项目。该项目的目标是创建一系列符合 ECMA 标准（Ecma-334 和 Ecma-335）的 .NET 工具，包括 **C# 编译器**和**通用语言架构**。与微软的 .NET Framework（共通语言运行平台）不同，Mono 项目不仅可以运行于 Windows 系统上，还可以运行于 Linux，FreeBSD，Unix，OS X 和 Solaris，甚至一些游戏平台，例如：Playstation 3，Wii 或 XBox 360


因此，为了提升.NET的平台适应性，微软在.NET发展之初就建立了一套对于.NET中间语言的实现规范——**.NET Common Language Infrastructure**，这相当于一套关于.NET中间语言（IL）的语法手册，微软希望通过这种方式让第三方和开源社区来参与.NET的平台移植。

**Ximian公司是最早参与这项工作的成员之一，并于2004年6月发布了第一代.NET跨平台产品——Mono 1.0。**

Mono与微软官方的CLR一样，都是对 .NET CLI（Common Language Infrastructure）的实现，他们都能对.NET的中间代码（IL）提供实时编译。不同的是，CLR只支持Windows系统，而Mono如今已支持包括Windows、Linux、macOS、iOS、Android在内的各种主流平台和操作系统。

著名的游戏引擎Unity3D就包含了Mono，我们所熟知的《Tample Run 神庙逃亡》、《炉石传说》、《Deemo》等游戏都是基于Unity3D开发的（包含.NET和Mono的技术）。

> 值得一提的是，Mono是一个有故事的项目，十几年来历经波折，几经转手，于2011年落入Xamarin公司手中，其间Mono还与微软发生过专利纠纷。

> 终于在 2016年2月，微软正式收购Xamarin，从此Mono回到了微软霸霸的怀抱，成了亲生儿子，同时微软宣布Mono面向社区免费。在2016年11月的Connect(); //2016开发者大会中，微软还发布了基于Xamarin Studio改造的Visual Studio for mac。

>  看看Mono这么牛逼 可以在微软闭源的情况下，还让.NET 跨平台的 他到底是怎么个牛逼法呢。 
这就牵扯到了一个问题“.NET 应用程序是怎么运行的？” 想知道答案的朋友们可以去好好看 ** [魅力 .NET：从 Mono、.NET Core 说起](http://www.cnblogs.com/xishuai/p/mono-dotnetcore.html)**


# Xamarin
考虑如何生成 iOS 和 Android 应用程序时，许多用户都认为本机语言、Objective-C、Swift 和 Java 是唯一的选择。 但是，在过去几年中，一个全新的生成移动应用程序平台的生态系统已经出现了。
Xamarin将.NET的强大功能和生产力带入iOS和Android，重用技巧和代码，同时获得本地API和性能。
Xamarin 是唯一能通过提供跨 iOS、Android 和 Windows Phone（Windows Phone 的本机语言已经是 C#）这三种平台可正常工作的单一语言 - C#、类库和运行时，却仍能编译性能甚至足以满足高要求游戏的本机（非解释型）应用程序的平台。
                                                **来一张对比图**
![image.png](https://upload-images.jianshu.io/upload_images/1979022-4a0845ef5c369abb.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)

Hybrid 是指混合开发，目前的ionic 、weex、MUI 均在此列表中。

React Native  是Facebook推出的基于React的做的框架，也很生猛目前在社区的生命力很旺盛。



#.NET Standard
某明奇妙提到的这个 .NET Standard 其实是未来的.NET 核心，一切基于它来实现代码的共享。
> .NET Standard 进一步实现跨平台跨设备的代码共享

.NET Standard 是一组由 .NET 实现的基类库实现的 API。 更正式地说，它是构成协定统一集（这些协定是编写代码的依据）的特定 .NET API 组。 这些协定在每个 .NET 实现中实现。 这可实现不同 .NET 实现间的可移植性，有效地使代码可在任何位置运行。

.NET Standard 也是一个目标框架。 如果代码面向 .NET Standard 版本，则它可在支持该 .NET Standard 版本的任何 .NET 实现上运行。


# .NET Core

> 最后，终于来到了现在火热的.NET Core 。

自 .NET Framework发布至今已有十余年，由于微软过于保守的版权策略，.NET一直作为Windows平台的封闭产品。尽管有Mono项目对.NET实现了平台移植，但毕竟不是微软“亲生”，Mono在一些实现上仍然不够完美。

随着2014年Xamarin和微软发起.NET基金会，微软在2014年11月份开放.NET框架源代码。随后在.NET开源基金会的统一规划下诞生了 .NET Core。

（注：.NET Core早期被称为 .NET vNext或 .NET 5，直到2016年1月才正式命名为 .NET Core 1.0）

需要注意的是，尽管微软把 .NET Core作为.NET未来的发展方向，但 .NET Core和 .NET Framework仍然是两个独立的产品。.NET Framework也会继续更新和维护。

.NET Core与 .NET Framework最大的区别在于 .NET Core是完全开源的，托管在github上，支持任何人向项目贡献代码。并且，.NET Core不再是Windows独占，还支持Linux、macOS等多种平台。

而 .NET Core 是.NET Framework的新一代版本，或者说是其进化版本，是微软开发的第一个跨平台 (Windows、Mac OSX、Linux) 的应用程序开发框架（Application Framework），未来也将会支持 FreeBSD 与 Alpine 平台。.Net Core也是微软在一开始发展时就开源的软件平台，它经常也会拿来和现有的开源 .NET 平台 Mono 比较。

由于 .NET Core 的开发目标是跨平台的 .NET 平台，因此 .NET Core 会包含 .NET Framework 的类库，但与 .NET Framework 不同的是 .NET Core 采用包化 (Packages) 的管理方式，应用程序只需要获取需要的组件即可，与 .NET Framework 大包式安装的作法截然不同，同时各包亦有独立的版本线 (Version line)，不再硬性要求应用程序跟随主线版本。

> **2016年6月27日 在RedHat DevNation  峰会上宣布了 .NET Core & ASP .NET Core 1.0 RTM 的发行。**
而目前最新的 .NET Core 版本为2.1.4。

> .NET Core的核心点： 创新、开源、跨平台

 
## 用更少的时间做更多有趣的事情 

**Develop high performance applications in less time, on any platform.**
翻译后：用更少的时间，在任何（全）平台上开发高性能应用程序。
以上描述说的就是 .NET Core。

 参考链接：[Develop high performance applications in less time, on any platform](https://www.svmsystems.com/single-post/2017/07/11/Develop-high-performance-applications-in-less-time-on-any-platform)



### 特点如下：
- #### 跨平台
您可以创建在Windows，Linux和MacOS上运行的.NET Core应用程序。
- #### 统一
利用统一的.NET标准库(.NET Standard)，使用相同的代码定位所有平台，并使用相同的语言和工具重用您的技能。
- #### 轻量级
没有影响部署和模块化开发模型，您只需要依赖于您所需的最少组件包。
- #### 现代
多语言支持C＃，VB，F＃和现代结构，如泛型，语言集成查询（LINQ），异步支持等等。

- #### 开源
运行库，库，编译器，语言和工具都是GitHub上的开源代码，接受代码贡献，测试和完全支持。





# .NET Core   与其他平台的关系
.NET Core 经常会拿来与其他平台做类比，尤其是它的源头 .NET Framework 以及另一个相似性质的开源平台 Mono。
为了让大家，更好的理解下，我阐述下吧。

#### .NET Framework

据微软的帮助，.NET Core 和 .NET Framework 是子集 (Subset) 与超集 (Superset) 的关系，.NET Core 将会实现出部分的 .NET Framework 功能 (基本上是不含用户界面的部分)，例如 JIT (.NET Core 采用 RyuJIT)、垃圾收集器 (GC) 以及类型 (包含基本类型以及泛型类型等)[10]。未来 .NET Framework 和 .NET Core 也将会是各自发展，但它们也会同时使用彼此的功能，例如 .NET Compiler Platform 与 RyuJIT 等技术。
#### Mono
Mono 是另一个已发展许久的 .NET Framework 跨平台开源版本，基本上并不隶属微软官方，而是由社区的力量所主导，自成一个生态系统，也开发出了像Xamarin这样的跨平台.NET移动应用，.NET Core 与 Mono 未来会是合作的关系，Mono 仍会维持社区力量的维护与发展，而 .NET Core 则会以官方角度来进行发展，两边也会一起进行彼此功能上的增进。
 
#### .NET Core 与 ASP .NET Core 的关系
其实一开始并不是主从关系 [11]，ASP.NET Core 的开发初期 (ASP.NET 5) .NET Core 还没有开始起跑，因此 ASP.NET Core 当时有自己的运行期与工具，一开始称为 Project K，后来改为 DNX (.NET Execution Environment)，DNX 本身就具有可独立运作的运行能力，不需要依赖 .NET Core 运行，但是这样会变成 .NET Core 和 ASP.NET Core 双头马车的现象，在 .NET Core 逐渐成熟之后，微软也决定要将这两个各自独立发展的产品线集成在一起，DNX 也将因改用 .NET Core 运行期而终止开发，DNX 的功能将由 .NET Core 以及旗下的 .NET CLI 接替提供，集成后的版本将在 1.0 RC2 时发布。




# ASP .NET

严谨来说，ASP.NET本不应该放在此处与以上三个框架平行，但是因为ASP .NET太出名了，因此我不得不在这说清关系。

ASP.NET最初是.NET Framework框架中的一个组件，用于开发Web应用程序。它是ASP技术的改进版本，需要注意的是，ASP与ASP.NET是完全不同的两个产品。同理，VB和VB.NET也是完全不同的两个产品。ASP和VB都是上个世纪的技术，过于古老在此不再赘述，但请务必注意区分它们。

早期的ASP.NET提供一种叫做WebForm的方式用于呈现网页，它可以让网页开发变得像WinForm开发一样简单且可视化。但由于WEB技术的飞速发展，WebForm由于其低效、封闭和难以定制的缺陷已经逐渐淡出历史舞台。

随着.NET 3.5的发布，微软提供了全新的ASP.NET网页呈现方式，称为ASP.NET MVC Framework。这套框架遵循MVC设计模式思想，将视图和逻辑进行了很好的分离，并且大幅提升了性能和可定制性。

经过多年发展，目前已经更新到了ASP.NET MVC6，MVC6完全采用.NET Core的项目结构，支持Framework、Core、Mono多种运行时。因此，ASP.NET MVC6也被称为ASP.NET Core。

 # ASP.NET Core
#### 历史的进程
ASP.NET Core 是新一代的 ASP.NET，早期称为 ASP.NET vNext，并且在推出初期命名为 ASP.NET 5，但随着 .NET Core 的成熟，以及 ASP.NET 5 的命名会使得外界将它视为 ASP.NET 的升级版，但它其实是新一代从头开始打造的 ASP.NET 核心功能，因此微软宣布将它改为与 .NET Core 同步的名称[1]，即 ASP.NET Core。

ASP.NET Core 可运行于 Windows 平台以及非 Windows 平台，如 Mac OSX 以及 Ubuntu Linux 操作系统，是 Microsoft 第一个具有跨平台能力的 Web 开发框架。

微软在一开始开发时就将 ASP.NET Core 开源，因此它也是开源项目的一员，由 .NET 基金会 (.NET Foundation) 所管理。
### 现在的责任
ASP .NET Core 是一个跨平台的高性能开源框架，用于生成基于云且连接 Internet 的新式应用程序。
 使用 ASP.NET Core，可以：
- 生成 Web 应用和服务、IoT 应用和移动后端。
- 在 Windows、macOS 和 Linux 上使用喜爱的开发工具。
- 部署到云或本地。
- 在 .NET Core 或 .NET Framework 上运行。

![image.png](https://upload-images.jianshu.io/upload_images/1979022-662d018b7b771f30.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


>注1：随着.NET技术的发展，时至今日，广义的 .NET指包含.NET Framework，.NET Core，Mono在内，是基于.NET技术的整个产品系列。而在过去的习惯中，.NET通常特指.NET Framework这一个最正统的框架。

>注2：.Net Core也有两重概念，广义来说，Core指全新的一整套框架，包括运行时，命令行工具，项目结构定义等等。Core结构的项目，支持指定Framework、Mono或者Core中的一者或多者作为运行时环境。而狭义上的Core，仅特指 .NET Core CLR（运行时）。请根据上下文和语境区分其定义。

# 如何在Windows，Linux和macOS上选择顺手的.NET开发工具.

如果您不确定从哪里开始？我们建议尝试[Visual Studio](https://www.visualstudio.com/)。

 
### Visual Studio
Windows上的全功能集成开发环境（IDE），用于构建各种类型的.NET应用程序。宇宙最强大的编译器。
 

### Visual Studio Code
在Linux，macOS或Windows上开发以构建跨平台网站和服务。安装C＃扩展以获得最佳体验。
 

### 适用于Mac的Visual Studio
使用Xamarin构建原生Android，iOS，macOS和Windows应用程序，以及使用ASP.NET Core创建网站和服务。
 

### OmniSharp
编辑器中的跨平台.NET开发，如Atom，Brackets，Sublime Text，Emacs和Vim。
 

### JetBrains Rider
使用IntelliJ和ReSharper技术构建的跨平台.NET IDE。它为所有平台上的.NET和.NET核心应用程序提供支持。
 

### .NET Core CLI
用于在Linux，macOS和Windows上开发跨平台网站和服务的命令行界面（CLI）。



### 尾声

最后推荐一本小书：《.NET 传奇：封闭到开放的历程》
 所以2018全面扑腾到 .NET CORE吧 !

顺带一提，您如果在文章中看到一些错误和疏漏，还请指出，或者到github上进行修改提交PR。非常感谢。


![image.png](https://upload-images.jianshu.io/upload_images/1979022-9d486f356944f856.png?imageMogr2/auto-orient/strip%7CimageView2/2/w/1240)


我们再回过头来看这张图是不是清晰了很多呢。

#### 参考文献：
 
https://en.wikipedia.org/wiki/Mono_(software)
https://wc.yooooo.us/wiki/.NET_Core
http://www.cnblogs.com/xishuai/p/mono-dotnetcore.html
http://www.jubeat.net/2016/09/25/dotnet-core-prologue/
https://wc.yooooo.us/wiki/.NET%E6%A1%86%E6%9E%B6
https://wc.yooooo.us/wiki/ASP.NET
https://wc.yooooo.us/wiki/ASP.NET_Core
