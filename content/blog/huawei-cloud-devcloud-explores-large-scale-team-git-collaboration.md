---
title: "华为云 DevCloud 在大规模团队 Git 协作的探索"
date: 2019-11-21T00:40:28+08:00
description: "华为在大规模团队的Git协作上的一些探索。"
bgImage: "images/backgrounds/blog-bg.jpg"
bgImageAlt: ""
image: "/images/blog/huawei-cloud-devcloud-explores-18.webp"
author: 孙超
postType: "演讲"
type: "post"
summary: "华为在大规模团队的Git协作上的一些探索。"
categories: 
  - "演讲"
tags:
  - "DevOps"
  - "Git"
  - "DevCloud"
---

> 本文内容选自中国 DevOps 社区年会 · 2019 年会，华为云孙超老师分享的《华为云 DevCloud 在大规模团队 Git 协作的探索》实录。

大家好！我是来自刚才熊节老师吐槽过的华为公司，但是我相信熊节老师如果现在去华为的话，应该可以看到华为的流程已经是越来越标准化了，尤其是刚才熊节老师的说需求管理这一块，现在我们去看一下的话，应该是比当初看到华为是不一样的了。我今天的主题大概在今年 10 月份在上海的 QCon 分享过一次，当时是有 45 分钟的时间，但是我今天的时间只有 15 分钟，所以按照乔梁老师说的，我今天要用3倍的速度来完成这个 PPT 的分享。

华为这几年承受了很多外界的压力，尤其像今年一开始某国就开了对华为展开了各种攻势，部分国家或地区也会以华为的产品可能存在安全问题为由，禁用华为产品。那么华为的产品确实是很多，包括路由器、交换机、芯片、手机、数据库、服务器、云产品等等，我们的产品很多，对应的源码也很多，要能够在这些国家和地区进行产品销售，那么我们要证明我们的产品是可信的，是安全的。如何证明我们的产品是可信的？我们就要证明我们的产品通过同样的发布过程能够获取到同样的产品版本，也就是从源代码下载这一步开始，到后面所有的编译打包，包括发布的整个过程，都是有迹可寻的，都是可见和可重现的。

今天就讲一下在这个背景下，华为在大规模团队的 Git 协作上的一些探索。首先自我介绍一下，我是 2015 年入职华为，在华为入职之后一直是在代码托管领域工作。华为内部的代码托管平台叫 iSource，是 DevCloud 旗下 CodeHub 代码平台的内部版本，我目前担任 CodeHub 的 committer。

![](/images/blog/huawei-cloud-devcloud-explores-01.webp)

首先大家可以思考一下这三个问题。上面两个问题可能是大家经常会遇到的，第一个是当你们的产品或者你们的项目涉及到 2 个及以上仓库的时候，如何做到代码库相互之间版本的关联？第二个，当有多个人同时在修改多个仓库的时候，如何管理这些这些仓库的分支与 Merge Request ? 最后一个问题其实就是华为很多产品在最初切换 Git 代码库的时候面对的一个问题，我们有的产品部门有几千个开发人员，同时要修改几百个仓库，并且同时开发着几百个特性，这个对于我们代码库的管理来讲其实是很棘手的。下面我会用10分钟的时间，说明一下我们在这类问题上的探索和关键的实践。

首先我们看一下现在华为内部 iSource 代码平台的规模，现在华为的正式员工包括合作方员工加起来已经注册有 20 多万人，我们的日活用户大概 2 万多。现在所有的代码仓库加起来大概是 60 万多。

![](/images/blog/huawei-cloud-devcloud-explores-02.webp)

然后大部分项目的规模是特别大的，好多产品部门下面会有几百个代码仓库，然后这些仓库的授权是特别细的，并且耦合非常紧密，特性分支特别多。另外我们发现有些仓库特别大，能达到 10 多个 G。华为的开发团队多数是跨网络分区的，比如说华为国内的研究所有深圳、北京、上海、杭州等，很多团队在开发的过程中，下载的仓库都要跨很多网络分区。我们仓库的构建频率非常高，每天可能要构建几百万次，在高峰期的下载频率能够达到 1 万次每秒。每天的代码下载量，我们统计过最多有 60TB 多，开发人员每天上传的代码量大概 100 GB。我们后台统计的 RPC 请求 6000 W/天，然后 Git 操作次数，例如上传下载大概是 640W 次/天。

![](/images/blog/huawei-cloud-devcloud-explores-03.webp)

刚才说的这个数据大家可以在知乎上找到相关的文章。在知乎上有一篇文章是《如何看待华为的 1100 亿行代码》，大家如果感兴趣的话可以去搜一下。

最开始华为内部转型使用 Git 是在 2014 年，大部分产品的代码仓库开始是托管在 SVN 上的，那我们用Git来进行切换，由于 SVN 和 Git 之间的特性的差异，我们就必须要对 SVN 仓库进行分解。我们面临的第一个问题就是多仓库的关联问题，我们一个产品线的仓库，会从 SVN 分出来几百个仓库，最开始我们使用的仓库关联工具是 Git 的 submodule。这个工具我们发现有三个问题。

![](/images/blog/huawei-cloud-devcloud-explores-04.webp)

第一个就是 submodule 要使用 gitlink 这么一个文件来关联仓库，但是这种关联的方式会导致子仓库修改的时候，都要连带主仓库一起提交。有时候多个项目组同时修改同一个子仓库会产生冲突。之前 有一个 CMO 同事跟我说，他一天的时间有半天的时间在解决冲突，这个问题是挺严重的；另外一个就是 submodule 它是使用 `.gitmodules` 文件完成仓库和代码目录的关联。使用这个文件，我们要用到 submodule 的一些命令，说实话这个命令使用起来是非常复杂的，好多使用 Git 很多年的一些同事，每次使用这些命令的时候都要去重新阅读，翻一下手册；还有一个就是我们在下载的时候，子仓库只能等到主仓库下载完之后，才能进行后续的下载，非常影响仓库的下载效率。

另外一个问题是，最开始我们的仓库是使用 fork 模式来进行代码提交，这个是经典的分布式的开发模式。我们的产品某个仓库开始会有一个主线仓库，然后每个子开发部门会 fork 出自己的仓库，再到下面的每一个项目组也进行 fork，然后项目级下每个开发人员再 fork 一次，提到代码的时候我们的方向是反过来的。这个时候有一个问题，当这个 fork 仓库的容量非常多的时候，你的仓库管理就会产生失控的现象，fork 出去的仓库，可以自行改 hooks 的规则，包括人员的一些权限。经常遇到某个 fork 仓库修改了规则，合并了一些提交，最终修改提交到这个主仓库的时候，才发现代码可能是有问题，已经不不符合主仓库的规则要求。那我们看一下github，你使用 fork 仓库创建的 Pull Requset 结束后，通常会建议你去删除 fork 仓库。

![](/images/blog/huawei-cloud-devcloud-explores-05.webp)

再有一个，fork 会引入另外一个问题。就是跟上游仓库进行同步实际上可能会比较困难，同步的方式大家可以看一下左边这个示例，我们可以通过命令行进行同步，这个过程中通常会遇到各种各样的冲突，解决起来可能会非常复杂。有些代码平台在页面上提供了反向 Merge Request 的功能，但是如果遇到冲突的情况，有时候还是要回到命令行来解决。当然如果你有 100 多个仓库要管理的时候，你肯定要 fork 100 多个仓库，这个同步过程是非常令人厌烦的一个过程。那如果我们不使用 fork 仓库，我们使用分支呢，也会遇到一些问题。比如因为分支全局可见，管理起来会非常混乱，然后分支特别多的话，后台就会容易有过多的分散引用，导致仓库下载非常慢。

![](/images/blog/huawei-cloud-devcloud-explores-06.webp)

还有就是 fork 派生容易导致磁盘消耗特别快，一般仓库跟刚刚 fork 出来的时候，它的存储是处于最优的情况。当你的派生仓使用了一段时间之后，它的这个文件句柄链接就会发生转移，最终会产生冗余的一些内容。华为在 2016 年发现一个仓库派生了 2000 多次，然后我们做了一次 GC，花了 2 天时间，释放了将近1TB的磁盘空间，所以 fork 也是我们希望解决的一个问题。

![](/images/blog/huawei-cloud-devcloud-explores-07.webp)

最终我们是希望不使用 submodule，不使用 fork 来提交代码，然后我们也不希望仓库产生那么多的开发分支。

华为内部做过很多架构上还有用户界面上的优化，最终影响最大的就是对标 Gerrit 平台，我们实现了叫做 OMEGA 的开发模式。OMEGA 是一站式多用途的 Git 协议的简写，是我们基于 Gitlab 的社区版本，进行改造的一种开发模式。

![](/images/blog/huawei-cloud-devcloud-explores-08.webp)

那么可以看一下 OMEGA 这种开发模式的特点，在代码合并上我们首先不需要 fork，而是通过客户端工具直接把修改推送到代码平台上，产生 Merge Request。还有使用一个叫做 manifest 的清单文件来维护仓库关系，不再使用 submodule 来实现版本关联了。OMEGA 有一个客户端叫做 git-mm，mm 是多模块的意思。

为什么我们不用 Gerrit？有三个主要的原因，一个是 Gerrit 它的项目管理是碎片化的，不太适合华为的产品仓库场景，同时授权方面也会有跨服务器的问题。最后一个是我们可能希望在华为代码平台上有更多的社交化的属性，因此 OMEGA 是基于gitlab的社区版本进行了二次开发。

那我们现在说一下 OMEGA，刚才说的这个开发模式，看起来是什么样子呢 ？首先我们在代码平台上会有一个 xml 清单文件，来描述子仓库的关系。

![](/images/blog/huawei-cloud-devcloud-explores-09.webp)

这个xml文件的第三行的 remote 是代表我们代码仓库服务器的地址，下面有 project 节点列表，左边红色的内容是代表了仓库的名称，右边的蓝色的内容是代表这个仓库下载下来解压的目录。我们会有一个工具，分析这个 xml 文件，把服务器上的仓库下载到本地。这个工具就是刚才提到的多模块的工具git-mm。

我们需要把这个清单文件放到服务器的一个仓库里面，然后用 git-mm 的 init 与 sync，自动地把列表中所有的仓库下载到本地。下载完毕之后，就可以看到本地的目录已自动按照我们的定义创建好了。开发人员下一步进行开发的时候，用 start 命名在本地产生个人开发分支，这个开发分支不需要在服务器上存在，只需要在本地创建就好了。接下来开发人员就可以在本地进行一些修改和Git提交。最后可以通过一个 upload 命令，一条命令把本地的提交推送到服务端并产生 Merge Request。最终我们看一下 upload 命令结束的输出内容：

![](/images/blog/huawei-cloud-devcloud-explores-10.webp)

每个代码仓库都有一个 Merge Request 的 URL 链接，并且最后有一个总的 Merge Request 容器。我们打开下面这个容器的 URL 之后，会看到这一个页面：

![](/images/blog/huawei-cloud-devcloud-explores-11.webp)

这个页面上可以看到所有代码仓库的Merge Request 链接，并且开发人员本地创建的开发分支会变成Merge Request 的描述内容的一部分，分支并不会在服务端真实存在的。

总体上 OMEGA 的工作流程就是这样的，开发人员不需要 fork 仓库。通过 init 和 sync 下载所有的仓库，然后在本地创建一个分支，进行相应的开发工作，最后通过 upload 把修改推送到代码平台的服务器上，产生一个Merge Request。同时平台发送消息给相关的 pipeline server，启动相应的 CI 工程。如果 CI 工程不通过，或者 committer 审核不过的话开发人员可以进行修改并更新 Merge Request，没问题的话就可以删除本地的开发分支，进入下一步的迭代开发。

![](/images/blog/huawei-cloud-devcloud-explores-12.webp)

同时在 pipeline server 上可以通过命令来记录各个仓库的快照情况，我们记住这个快照之后，就可以对每条 CI 的结果，每次代码检查的结果 ，包括发布的每一个产品的版本，进行源码回溯。我们可以通过这个快照，完全还原当时构建的时候每个仓库对应的一个提交点。

![](/images/blog/huawei-cloud-devcloud-explores-13.webp)

后面推广了 OMEGA 这种集中式开发模式后，开发人员不再需要 fork 了，效率确实有很大提升。但使用了集中式的仓库管理模式之后，我们也发现了一些问题，主要集中在服务端。我们发现所有的开发人员往同一个仓库提交，后台会产生大量的 pack 文件，这些 pack 文件可能会包含重复的内容，为加快 git gc 的速度，我们会首先使用 `git pack-redundant` 命令来去重，结果发现这个命令会导致 CPU 和内存耗尽。最终定位到是源码中使用的算法问题，在优化了代码并推送到社区后，我们解决了这个问题。

![](/images/blog/huawei-cloud-devcloud-explores-14.webp)

另外我们发现非常频繁的操作同一个仓库，会导致刚刚更新的分支丢失最新的 commit。比如下面这个例子，master 分支最开始指向 V1 版，有修改之后指向 V2 版本，再修改就是指向 V3，但经常发现这么一个情况， master 分支突然又回到 V2 这个版本。这个最终也是通过了一段时间的分析之后，我们发现这是一个源码的 BUG，最终也是把这个修改推送到了社区。

![](/images/blog/huawei-cloud-devcloud-explores-15.webp)

那么我们回到可信这个话题，就是我们这个集中开发模式到底对我们说的可信有什么帮助？

![](/images/blog/huawei-cloud-devcloud-explores-16.webp)

首先我们用 manifest 替代 submodule，我们可以进行仓库关系配置化；另用一个仓库不需要 fork，我们能够统一管控所有的仓库，包括规则我们都是统一管控的。另外 manifest 这个文件列表之外的仓库，我们不参与构建与发布，我们可以确定我们的仓库来源是可信的。还有在 pipeline server 上，我们记录了所有仓库的快照信息，对应的 CI，代码检查，包括我们的产品版本都是可以回溯的，是进行复原，可重现的。

华为云 DevCloud 旗下的 CodeHub 代码平台，在今年年底的时候，我们会上线 OMEGA 开发模式。

![](/images/blog/huawei-cloud-devcloud-explores-18.webp)

希望大家也关注一下 DevCloud 的相关产品的特性发布。DevCloud 提供了一站式 DevOps 的各种工具与平台，包括我们的项目管理，代码托管、CI 流水线，代码检查、编译构建，包括相关的测试工具，包括版本的发布管理，以及云端的 CloudIDE。希望大家以后对华为云 DevCloud 相关的产品多一些关注，谢谢大家。

#### 关于作者

<center>
![](/images/blog/huawei-cloud-devcloud-explores-17.webp)

孙超

华为云

BU 代码平台 Committer
</center>
