---
title: "大规模微服务场景下灰度发布与流量染色实践"
date: 2019-12-01T09:14:00+08:00
description: "本文内容选自中国DevOps社区年会 · 2019年会，刘超老师分享的《大规模微服务场景下灰度发布与流量染色实践》实录。"
bgImage: "images/backgrounds/blog-bg.jpg"
bgImageAlt: "ALT-txt"
image: "/images/blog/nsf-01.jpg"
author: "刘超"
postType: "演讲"
summary: "本文内容选自中国DevOps社区年会 · 2019年会，刘超老师分享的《大规模微服务场景下灰度发布与流量染色实践》实录。"
type: "post"
categories: 
  - "演讲"
tags:
  - "微服务"
  - "灰度发布"
  - "流量染色"
---

>本文内容选自中国DevOps社区年会 · 2019年会，刘超老师分享的《大规模微服务场景下灰度发布与流量染色实践》实录。

![](/images/blog/nsf-01.jpg)

大家好，我的题目叫《大规模微服务场景下的灰度发布与流量染色实践》。最近微服务很热，与微服务相关的架构、流程、DevOps都很热。

![](/images/blog/nsf-02.jpg)

很多公司，包括传统企业，到互联网公司做交流的时候，会问道，你们互联网公司号称能够加速业务创新、快速迭代，那我们是否也可以引入类似这样的机制。

我们做微服务，主要分为两个方面，一个是业务方面，另一个是技术方面。最下面是运维部，不过现在我们的运维部已经拓展成云计算，DBA里的数据管理部门，已经发展成大数据，于是就有了技术中台和数据中台，另外还有共享用户中心的业务中台，总体构成了下层的中台部门，在上层业务一定要做微服务化。业务和技术互相合作，做到加速创新的效果。

![](/images/blog/nsf-03.jpg)

有很多人说，我们也上了微服务，但是会发现上微服务以后，看起来很好的东西，为什么用起来一团乱麻。

我们拜访过很多业界同仁，发现实施微服务之后，有以下痛点：

服务依赖管理：服务间直接调用，**依赖混乱**（微服务越来越多，自己理不清楚，不知道上线时会影响谁，上线后谁影响我，到底该什么时候上线，依赖混乱的时候，没办法解决这些问题。）

服务调用统计：**调用记录**无迹可寻，调用统计与分析无从谈起

服务接口规范：环境与接口**规范缺失**，维护困难

服务安全管理：安全靠白名单各自为战

服务治理能力：大量**重复代码** 实现路由，分流，熔断，降级

服务接口测试：拆分过程中接口**行为不一致**，隐藏Bug

服务灰度发布：上线功能实现灰度借助大量**if-else**

服务压力测试：对于峰值压力**无历史数据**，靠运气

服务调用链分析：当服务请求缓慢，**难以定位**问题点

测试环境治理：测试**环境多，难管理**，不可能100个容器每组一套

![](/images/blog/nsf-04.jpg)

我们发现大家对微服务有很多误解。比如，一般做微服务的时候，很多人都会问微服务怎么拆，告诉我一个拆的最佳的实践，但是其实，根据我们的实践来讲，微服务不仅仅是微服务拆分，微服务拆分只是十二个要点的其中之一。

**十二个要点分别是：**

1. 微服务化的基石：持续集成

1. 静态资源分离与接入层设计

1. 应用层设计之无状态化与容器化

1. 应用层设计之服务的拆分，发现与编排

1. 性能优化之数据库设计与横向扩展

1. 性能优化之缓存的设计与横向扩展

1. 性能优化之消息队列与异步化设计

1. 服务的熔断，降级，限流设计

1. 配置中心的设计与实践

1. 统一日志中心的设计与实践

1. 全链路应用监控实践

1. 服务的全链路压测实践

我们建议，先把前三个基础打好，再进行拆分，而不是什么技术、平台、工具都没有，直接把自己的传统应用拆得七零八落。**同时，值得再强调的是第一条，微服务化的基石：持续集成。微服务绝不是让大家关起门来用三个月的时间拆出来，就直接上线。而是应该不断地集成、迭代，是渐进式的模式。**另外，微服务也不仅仅是个技术问题，它还涉及到IT架构、应用架构、组织架构的改变。

![](/images/blog/nsf-05.jpg)

接下来给大家讲一下网易微服务和DevOps的实践过程。

**我们整个DevOps，也是经历了几个过程。第一个和大家都一样，当服务比较少的时候，开始手工化的方式，后来手工不行了就变成了脚本化的方式，再后来因为开源有很多的工具可以用，变成了工具，而后变成一个平台，最后变成一个统一的DevOps的平台。**

![](/images/blog/nsf-06.jpg)

首先，第一个阶段就是手工化。可能很多企业一开始都会存在这样的阶段，开发和运维之间的隔阂比较严重，老死不相往来。开发负责写代码，线上的运维、发布，以及SLA的保障，都是运维进行管理的。由于服务相对比较少，用物理机部署，基本上是一个单机应用加一个Oracle就可以搞定。

![](/images/blog/nsf-07.jpg)

后来，随着业务的发展，服务越来越多。这个模式和原来还是没有变，开发和运维部的隔阂依旧存在。但是，运维发现接的需求越来越多，需要部署越来越多，需要一个环境隔离的方式，因此一般会上一个虚拟化系统，业内主流是用Vmware。这时候的部署方式一般是，Oracle部署在物理机上，其他业务系统都是部署在VMware上。部署东西多了，运维开始使用批量脚本试图解放人力，这属于第二个阶段-脚本化的阶段。虚拟化带来很多的优点，比如，粒度灵活，隔离性得到一定保证，不会在一台服务器上部署很多东西。

但是这个阶段也有非常多的问题。比如说发布脚本、逻辑相对复杂，时间长了以后，逻辑是难以掌握的。而且，如果你想把一个脚本交给另外一个人，也很难交代清楚。

另外，并且脚本多样，不成体系，难以维护。线上系统会有Bug，其实发布脚本也会有Bug。

虚拟机大量地依赖于人工的调度，需要运维人员非常清楚，要部署在什么地方。另外VMware还有一个问题，它使用共享存储，会限制整个集群的规模，因为此时的应用不多，这个程度的规模还可以接受。

线上的高可用性，业务层的开发人员不会做任何事情，他认为是线上一旦出事，应该由运维集中处理，迫使运维服务的发布人员依赖虚拟化机制，来提供高可用机制。我们都知道VMware有非常著名的简化运维的高可用机制，比如FT、HA、DR等类似的机制。如果我们是从IT层来做高可用，有一个缺点，作为基础设施层来讲，它看上层没有任何的区别，所以没有办法区分业务优先级。比如说FT的模式，跑CPU指令，它不知道这是最核心支付的指令、还是日志的指令，再如数据中心之间的同步，存储层是无法区分交易数据和日志数据的。

另外网络、虚拟化、存储等基础设施，没有抽象化的概念，复杂度非常高，开发接不了这个工作，必须依赖运维，就要审批。由统一的一帮人来做，而且他们要考证书，比如，网络要有思科的证书，虚拟化要有VMware的证书，要特别专业才能做这件事情，因此会极大地降低迭代速度。业务方无论做什么事，都要走审批，运维部的人根本忙不过来，这是第二阶段的问题。

![](/images/blog/nsf-08.jpg)

后来是怎么改变了这个问题？首先是业务层，业务层接的需求越来越复杂，迭代速度要求越来越快，这个时候单体应用跟不上了，需要进入服务化的架构，工程要拆分，要开始基本的注册发现，要实现自己的RPC。

![](/images/blog/nsf-09.jpg)

应用层的改进会带来应用层的问题。比如，服务雪崩的问题。大量的请求堆积，一个进程慢了，把整个链路也都变慢了，所有人都在等着它缓过来。我们要进行熔断，快速尝试另外的服务。原来依赖很多内网负载均衡以及硬件负载均衡的维护代价比较大，一旦出现任何问题，就会引来抖动的问题。所以相应的要有快速恢复、快速熔断的机制，一旦发现错误以后，我们要能够尽快的重试。

![](/images/blog/nsf-10.jpg)

以上就是应用层的问题，经过了一段时间的解决，又引入了新的问题。**我把它称为“云原生怪圈”，应用向云原生的（Cloud Native）。**它包含两个层次，第一个层次是应用层的服务数目会增多。第二个层次是资源层申请速度的灵活性会相对增加，这两个层次形成了一个圈。每家公司可能都存在这个圈，无论是从哪个起点开始，这个圈都可能会被激活。

一个起点是，很多公司的上面是单体应用，但下面先采购了容器，资源申请灵活性大幅度提高了。一旦灵活性提高了以后，会给应用层释放很多动力。原来申请一百个机器需要一个星期的审批流程，这时能不拆分就不拆分。而现在有了容器，他会认为我有了这么好的工具，我可以进行拆分了，反正不费劲，任何一个小部门创建一个小的环境都不费劲。

另外一个起点，先是应用层服务数目增多，给资源层越来越大的压力，然后会使得你原来七八点下班，现在变成十点多下班，然后十二点下班，压力越来越大，就会想办法增加资源层的灵活性。这个圈在整个DevOps的过程中会一直产生的。

**微服务化了以后，我们会发现存在以下几个现象。**

第一个是服务器的机型非常的碎片化，一开始采购机器的时候，有大规格、小规格的，硬盘比例各不一致，导致服务器非常难以管理，也无法进行批量化的安装。

第二是很多的进程，不管是虚拟化以后，还是不虚拟化，在不在一台机器上，QoS无法保证。

第三是测试环境的需求量大大增加，下层的基础设施根本忙不过来。

![](/images/blog/nsf-11.jpg)

接下来进入到云计算的平台。有很多人不理解云计算和虚拟化都是运用了虚拟化的技术，两者之间到底有什么不同。其实云计算带来了非常大的不同，甚至是本质上的不同。如果你们内部上了一个云平台，或者上了公有云，但是你没有感受到资源申请的灵活性，那肯定是有些姿势用得不对。

这里，**我总结了一下云计算带来的改变，主要有三大方面，分别是统一接口、抽象概念，租户自助。**正是因为这三大方面，使开发和运维不像原来那样，有那么深的隔阂，而是开始逐渐互相靠近，开发部或者业务部开始进行一定的自助。

OpenStack实现接口统一，大部分部署工具支持其接口，可基于开源工具实现发布的工具化和平台化

Flavor抽象资源配比（4G 8G 计算优化型，网络优化型，存储优化型），统一硬件配置，提升利用率，硬件上线效率提升

自动调度代替人工调度，区域可用区抽象对机房机架交换机的感知

云提供租户概念，有账号子账号体系，有quota，可以让租户在管理员许可的范围内自助操作，加快环境部署速度

VPC屏蔽物理网络复杂性，冲突问题和安全问题，使得租户可自行配置网络

基于虚拟机分层镜像发布和回滚机制，构建发布平台，可实现大规模批量部署和弹性伸缩

基于虚拟机的PaaS托管中间件，简化租户创建，运维，调优中间件的难度

发布平台提供基于虚拟机镜像+PaaS中间件的统一编排

要求业务对于高可用性设计要在应用层完成

![](/images/blog/nsf-12.jpg)

在这个阶段，要实现微服务框架与开源技术栈的统一。一开始微服务做的比较混乱，有用Spring Cloud，有用Dubbo的，需要一个统一的开源技术栈。另外，还要构建一个持续集成的平台，通过Agent和虚拟镜像部署软件包。

![](/images/blog/nsf-13.jpg)

统一微服务框架之前，我们情况是这样的，一开始用服务注册服务发现，还是比较简单的。后来发现，我们还需要分流、需要降级、配置中心、认证鉴权、监控统计等，在业务代码之外加的越来越多，大家的代码写得到处都是，而且依赖于不同人的水平不一样，有的人写得好，有的人写得差，这就是一个当时遇到的问题。

![](/images/blog/nsf-14.jpg)

后来我们就把它抽象成为了一个Agent，这个Agent在程序启动的过程中，通过jar直接带起来，使得统一的服务框架组件在Agent里面实现，并且提供统一的界面进行配置，这样业务方可以只写业务代码，基本上就搞定了这件事。

![](/images/blog/nsf-15.jpg)

这样就形成了一个统一的微服务治理平台，并且后期会和service mesh做一定的融合。

![](/images/blog/nsf-16.jpg)

因此解决了这些问题：

**应用减负**：使用Agent和Sidecar技术，对应用无成本增强。

**开发减负**：以微服务治理框架为设计目标、大幅减少重复框架代码、避免重复造轮子。

**版本控制**：统一组件版本配置，避免隐性问题。

**兼容性**：兼容的HTTP、RPC调用，兼容非java应用。

**服务治理**：根据业务线场景选择治理支持方法级别治理粒度。

**高性能**：更低的性能损耗，并提供更细粒度的服务治理。

![](/images/blog/nsf-17.jpg)

这时就有了发布平台。我们会把包放统一的对象存储上，通过Agent以镜像的方式进行下发。

![](/images/blog/nsf-18.jpg)

这是我们的成果，内部都在用这款基于虚拟镜像的发布平台。

![](/images/blog/nsf-19.jpg)

接下来又引入了新的问题，比如难以发现故障点、要引入故障注入服务，API版本混乱，这时需要引入API网关。

![](/images/blog/nsf-20.jpg)

基于虚拟镜像的发布也很混乱，因为部署的应用越来越多，我们发现虚拟镜像的模板越来越多，会出现上千个无法复用的模板，好像每个小组织都有自己的一个东西，毕竟它还不是一个标准，所以接下来我们就拥抱了容器的标准。并且Auto Scaling原来是基于虚拟镜像的，现在使用Kubernetes来做，同时实现了分布式事务。

![](/images/blog/nsf-21.jpg)

到了这个阶段，中间加了Kubernetes这一层。这里的更新包括，OpenStack可以做物理机的下发，Kubernetes作为统一的对接资源的编排平台，无论是Vmware上，还是KVM机器上，还是物理机上，公有云上，上面都可以有Kubernetes统一平台。这个时候只需要对Kubernetes下发一个编排，就可以实现跨多个地方进行部署。

在基于虚拟机的运行环境和PaaS中间件之外，基于Kubernetes也可以有自己的容器镜像和运行环境，以及基于容器镜像PaaS中间件。发布平台原来是对接API的，现在有了Kubernetes以后，它可以非常平滑的通过统一的平台切换到Kubernetes上，所以，做一个发布平台，后面的对接还是比较标准的。

应用层也会越来越多，比如说有基于容器镜像的弹性伸缩，服务网格，分布式事务，故障注入等。

![](/images/blog/nsf-22.jpg)

有了Kubernetes以后，就进入了Dev和Ops的融合阶段。这时我们发现，当服务数目再增多的时候，运维的压力也更大，如果所有的东西都要运维来做，其实是实现不了的。因此，我们建议环境交付提前，比如说一个容器镜像里面的子环境让开发自己去把控。他知道自己改了哪些内容、哪些配置，不需要通过文档的方式交给运维来做。容器镜像还可以做一个很好的事，它是非常好的中介，是一个标准，不论在那儿都可以，所以就产生了左边的太极图。运维会帮开发部做一些事情，开发帮运维做一些事情，这个时候进入了开发和运维融合的机制。

![](/images/blog/nsf-23.jpg)

因为容器有非常好的分层的机制，如果开发不想写，可以让开发写大部分的基础环境。

![](/images/blog/nsf-24.jpg)

另外一个建议叫不可改变的基础设施。当规模大了以后，任何一个节点出现了问题，都很难排查，所以我们建议对任何环境的修改，都要在代码的级别上修改。在部署平台之前，代码是代码，配置是代码，单实例运行环境Dockerfile是代码，多实例的运行环境编排文件也是代码。

![](/images/blog/nsf-25.jpg)

持续交付流水线，是以Master和线上对应的，自己分支开发的模式。按需自动化构建及部署，线上环境还是需要人工触发的，但基本上是通过流水线代码处理的方式来做的。

![](/images/blog/nsf-26.jpg)

容器化带来的另外一个问题，就是“云原生怪圈”再次起作用。服务规模越来越大，增加速度越来越快，需求指数性增加，大家都需要一个环境。比如一个集群一千个容器，如果三个小组各开发一个项目，想并行开发，每个人都需要一个环境，一下子需要三千个容器。**这时候就需要中间件的灰度发布和流量染色的能力。**

![](/images/blog/nsf-27.jpg)
![](/images/blog/nsf-28.jpg)

在最外层的网关上，可以做两个环境之间流量的分发，以及在微服务的Agent里面也可以做一个分发。最终，我们会有一个基准环境，就是Master对应的环境。

![](/images/blog/nsf-29.jpg)

两个小组，一组开发了五个服务，另外一组开发了六个服务，他们部署的时候不需要一千个全部布一遍，只需要布五个，布六个。在请求调用的时候，从这五个里面互相调，不在这五个里面，在基准环境调，另外六个也是。这样就把三千个变成一千零十几个，环境大幅度减少。

![](/images/blog/nsf-30.jpg)

这个时候环境的合并怎么办？环境合并和代码合并逻辑一致，统一在发布平台管理，谁后合并谁负责Merge。这是我们的一个效果，我们节省了非常多的机器。

![](/images/blog/nsf-31.jpg)

**有了流量染色功能，就可以做线上的灰度发布。这里我们会有几个环境，一个是预发类的环境，一个是小流量环境，还有一个主流的环境，测试的时候是可以进行染色。**

![](/images/blog/nsf-32.jpg)

我们以一天的整个开发周期举例子，每天早上初始化预发环境和小流量环境＞＞开启引流，进入持续发布周期＞＞代码发布到预发环境进行回归，预发环境为单节点部署＞＞预发通过后发布到小流量环境，小流量环境三节点部署，滚动发布＞＞小流量环境，开发测试及时跟进，观察异常情况，一旦碰到问题，第一时间关闭流量入口。相关问题定位debug可以在预发环境上进行＞＞所有发布到小流量环境的版本合集，通过一个晚高峰的检测后，发布到线上环境。第二天同样是做此循环，每天都是这样的发布模式。

![](/images/blog/nsf-33.jpg)

有了流量染色以后，还可以得到单元化和多机房的染色。如果我们做高可用，至少需要两个机房，那么就存在一个问题，当一个机房完全挂了怎么办？微服务框架可以把它引流到另外一个机房。服务请求之后，还应该回来，因为应该本机房优先，毕竟本机房的容量大得多。**所以我们建议整个部署模式，总分总的部署模式。**

首先第一个总，要有统一的发布平台，无论发布到哪个Kubernetes，都应该通过一个平台。其次，你应该有一个多Kubernetes统一的管理，有多个机房，就有多个Kubernetes，我们并不建议跨机房。然后，我们建议应用层要有统一的视图，即使Kubernetes出现了问题，应用层可以把流量切到另外一个环境。就是这样一个总分总的模式。

另外Kubernetes也面临升级的问题，它更新比较快，经常升级。虽然业界有各种平滑的最佳实践，但是很难保证它升级的时候不出事。一旦Kubernetes出现状况，你也不想停里面的应用，可以采用分流的方式。

![](/images/blog/nsf-34.jpg)

**最终形成了云原生架构的技术栈，包括CICD、测试平台、容器平台、APM、分布式事务、微服务框架、API网关一栈式工具链。**

#### 作者
<center>
![](/images/blog/nsf-35.png" />

**刘 超**

**网易**

**杭州研究院**

**云计算技术部首席架构师**
</center>

长期致力于云计算开源技术的分享，布道和落地，将网易内部最佳实践服务客户与行业。
曾出版《Lucene应用开发解密》，极客时间专栏《趣谈网络协议》《趣谈操作系统》。