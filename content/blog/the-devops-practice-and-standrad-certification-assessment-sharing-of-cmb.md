---
title: "招商银行DevOps实践及DevOps标准认证评估分享"
date: 2019-11-15T11:53:11+08:00
description: "本文内容选自中国 DevOps 2019社区年会上滕乐英老师分享的《招商银行DevOps实践及DevOps标准认证评估分享》实录。"
bgImage: "images/backgrounds/blog-bg.jpg"
bgImageAlt: "ALT-txt"
image: "/images/blog/devops-cmb-0.png"
author: 滕乐英
postType: "演讲"
type: "post"
summary: "对于传统的金融行业的更新迭代，如何做才能更好？来看看招商银行是什么做的。"
categories: 
  - "演讲"
tags:
  - "DevOps"
  - "标准认证"
---

> 本文内容选自中国 DevOps 社区年会 · 2019年会，滕乐英老师分享的《招商银行 DevOps 实践及 DevOps 标准认证评估分享》实录。

大家好！我先自我介绍一下，我叫滕乐英，来自招商银行杭州研发中心。2005年加入招行，先是做了几年的开发，然后在2009年转做配置管理。从2014年开始，我们行开始接触 DevOps，我就开始从事 DevOps 相关的工作，直到现在。目前主要负责杭州中心及分行 DevOps 的实施与推广。今天我给大家带来的主题是《招商银行 DevOps 实践及 DevOps 标准认证评估分享》。主要从以下四个方面给大家做一个介绍：

- 第一部分，招行 DevOps 之困惑。

- 第二部分，招行 DevOps 探索历程。

- 第三部分，招行关键工程实践。

- 第四部分，DevOps 标准认证评估分享。

我们在 DevOps 实施初期，也是有一些困惑的，比如发布节奏。
![](/images/blog/devops-cmb-28.png)
早上我们也听了很多互联网企业的案例，是按天发布的，那么我们作为传统的金融行业，是否需要按照这么快的节奏去发布？是不是快就是好？这个问题需要我们不断去思考不断去实践摸索。所以关于发布节奏，我们这边是由开发人员和业务人员一起讨论商定的。目前一般是一个月发布一次，或者两周发布一次，这两种节奏也是业务和开发都比较容易接受的。
![](/images/blog/devops-cmb-27.png)
关于自动化测试，微软公司的单元测试覆盖率非常高，能做到100%全覆盖。这么高的覆盖率又是否适用于我们？从我们的角度，更多的还是希望开发通过实践，真正发现这个单元测试的价值，对他们的代码质量，包括线上质量确实有帮助，让开发自发地去做；而不希望像有的企业从上往下去强推。虽然说强推覆盖率能够很高，但是否能真正提高代码质量，提高效能？

当然，我们现在也在推自动化测试。好的自动化测试，在保障项目、产品质量的同时，也能带来效能上的提升。就像上午熊节老师说的要提升质量，就得做 TDD。我们现在也有团队在试点 TDD，后续还会继续深入探索，希望能有正向的结果数据反馈，继而扩大试点范围。
![](/images/blog/devops-cmb-02.png)
接下来，介绍一下我们在 DevOps 上的探索历程。之前在杭州的 Meetup 上介绍过我们自研的 DevOps 流水线平台。所以这次我就快速带过，我们是在2014年开始接触 DevOps。在这之前我们都是手工去做编译，比方说进入 UAT 之前，组织级配置管理员会在 UAT 构建机器上手工编译代码，将源代码转化成二进制文件。因为开发的话，他们基本上都是在本地编译，如果存在依赖包在本地，未上传配置库的话，在 UAT 构建机器上编译就会不通过。所以在2014年我们开始尝试把写手工编译的工作进行脚本化。由于不同的团队，能力会有差异，有些团队技术能力非常强，所以他们可以自己去写一些自动化的脚本。有些团队比较弱的，我们就会提供一些模板，然后开发根据这个模板去编写他们的自动化脚本。然后我们就开始尝试做持续集成。那个时候我们使用的是商业版的持续集成工具。

在2015年的时候，领导带队到国内外领先的敏捷企业去交流，看他们的敏捷实践具体是怎么落地的，包括 DevOps 这一块。我们开始尝试敏捷试点，扩大持续集成的试点，同时增加了两块技术实践，一块是技术债的管理，另一块是自动化部署。

然后到了2016年，这个时候我们的 DevOps 正式起步了，我们根据总结出来的实践经验，开始自研工具平台。之前采购了商业工具，虽然说有定制化，厂商入驻的工程师能力也很强，但由于工具框架的约束，总归还是没那么灵活，加上我们体量剧增，性能上也无法满足我们的要求了。所以这个时候，我们就开始思考，是不是自研才是出路。然后，我们开始打造综合管理平台，改进源代码管理工具，并持续推动开发降低技术债。

2017年，我们建立了内部的 DevOps 成熟度模型，持续推动 DevOps 实践落地，努力打造 DevOps 综合平台，包括持续交付流水线平台。

2018年，持续交付流水线平台成熟了，我们的工程实践也全面落地了。开始要求开放平台的同学必须通过流水线平台去跑构建，sonar 扫描，发布制品库，自动化部署，才能将TAG同步到我们的项目管理流程上，才能提上线申请，同时我们在流水线上也设置了一些管控点，比如说技术债的要求，开源漏洞要求等等。如果质量门禁不达标的话，这条流水线状态是红色的，是没法上线的。这一年，协同工作平台也逐步成型了。 

到了2019，也就是今年，一方面是优化提升我们具体的工程实践，另一方面是持续改进我们的工具链。另外继2018年参加了 DevOps 标准3.0评估之后，今年领导要求所有运营一年以上的敏捷团队都要参加 DevOps 标准 3.0的评估。一来是想通过外部的力量来驱动开发团队优化具体的工程管理过程实践。二来是帮助我们组织级找到工具链的改进方向，持续优化我们的工具链。最终还是希望能够从用户的角度出发，打造一套简单易用的综合管理平台。
![](/images/blog/devops-cmb-03.png)
这是我们的 DevOps 工具链，大家可以看到我们内部用的工具非常多，在项目过程管理这一块，我们目前主要是用 JIRA，基于 JIRA 商业版做了一层封装，来打造我们的协同工作管理平台，即电子看板。目前是两周一个迭代去做的。Tracker 这一块，我们是基于 IBM 的一个产品框架封装的一个工具，主要用来管理专题、迭代，还有一些度量数据缺陷等等。VP 主要是管理我们的项目管理流程，需求、立项、ST、UAT、上线流程全部都在 VP 上。Conference，这个可能很多企业都在用，这个主要是管理我们的知识库，比如我们的一些用户手册，还有一些比方说技术上的问题、解答都在上面。ITIL 是在数据中心那边的，主要用来管理项目的发布流程。在配置工具方面，我们也是逐步演进的。我们最开始用的是 FIREFLY。FIREFLY 管理操作很简单，但是它的功能还不够强大。后来我们引入了 IBM 的一套工具 CC、RTC。现在我们基本上用的是码云，是一套基于 Git 封装的工具。然后构建这块的话，我们目前这些都是集成在流水线平台上的。用 Sonar 来扫描我们的代码，做一些静态代码规范性检查。用黑鸭扫描开源漏洞，如果扫出一些中高危的漏洞，流水线会失败。然后还有一些就是单元测试的一些框架工具。在部署这块主要是用的 UCD。基础设施这块我们用的厂商也是非常多，大家可以看到，招行还是比较开放的，业界有什么好的东西，我们都是积极吸纳，所以我们现在有用微软的，亚马逊的，pivotal 的，当然还有一些虚机。然后沟通协作这块，招呼、移事通这两个都是我们自研的。流水线的执行结果，也会通过招呼订阅号推送给项目干系人。在可视化这块我们用的比较多的是 TableLu，基于这个工具我们做了招行的度量平台，可视化了各个层级的数据报告，希望能够做到数据驱动过程改进。
![](/images/blog/devops-cmb-04.png)
这是我们 DevOps 综合平台的全貌。主要分协同工作服务，持续交付流水线服务，统一配置管理服务，广义测试管理平台服务，运维/运营平台以及度量分析服务。

接下来重点介绍一下招行关键工程实践。
![](/images/blog/devops-cmb-05.png)
统一代码仓库，之前我们这边存在团队各自为政，私立“小仓库”,管理混乱，可读性不佳的问题，后来我们要求统一使用码云，并且统一规范，统一标准，易读易维护，也符合接入流水线的标准。
![](/images/blog/devops-cmb-06.png)
灵活的分支策略，由于不同的开发团队业务、开发模式会有不同，哪怕是同一个开发团队，分支使用场景也是又多又复杂，同时，分支这块是开发自主管理的，每个团队都有自己的个性化特点，所以从组织级层面看，是有点混乱的。所以现在组织级建议开发根据实际情况，采用灵活的分支策略，主推三种分支策略：分支开发、主干发布；主干开发，分支发布；主干开发，主干发布。明年会考虑制定一些分支策略与流水线套餐。
![](/images/blog/devops-cmb-25.png)
自动化编译。我们现在这块也是集成到流水线平台上，通过脚本或者是特定编译工具实现源码下载、编译。主要支持的框架有 Maven、Gradle，Ant 等等。然后主要支撑语言有 JAVA、C#、C++ 等等。这块我们不同于一些企业，之前我们去阿里的某事业部做过一些交流，他们为方便统一管理，选取的技术栈就是JAVA，大家统一用 JAVA 来编写代码。
![](/images/blog/devops-cmb-26.png)
但是我们行有非常多的遗留系统，所以这个技术栈和框架是非常多的，语言和版本也非常多，所以说管理起来非常复杂，构建环境也是非常复杂，所以支持成本非常大。我们现在加大力度基于 docker 和 K8s 建设持续交付流水线。实现编译环境的 docker 化和池化。定制了 CLI，可以自动探测编译语言和框架。
![](/images/blog/devops-cmb-07.png)
大家可以看到这个是我们基于镜像的流水线和 CLI。我们有非常多的 slave，支持动态快速创建，动态销毁。CLI 是标准化的，跨平台的，有自己的版本管理，可以动态加载配置，可以探索构建工具，然后可以自动升级，所以这块对用户来讲是非常简单易用的。持续交付流水线平台，现在我们是有两个版本，一个总行版的，一个分行版的。分行相对于总行能力相对会弱一些。但分行根据我们提供的这个操作手册去来配也是没有问题的。我们目前统计下来的话，国内一共有44家分行，有40家分行已经在用持续交付流水线平台。总行这边是所有的开放团队都在用。

我负责分行推广，和分行开发人员的交互会比较多，有一家分行主动联系我说用了分行云，持续交付流水线之后，他们的研发效能提升了很多。这对我们来说是个正向反馈，是对我们平台的肯定。
![](/images/blog/devops-cmb-08.png)
静态代码扫描，这块因为招行有很多遗留系统，不少遗留系统的技术债务是比较高的，并且规则很多，开发人员对规则的抵触情绪会非常严重。因为自由惯了，你现在加以约束，他们肯定是会不高兴的。并且会对这些规则提出挑战。尤其是引用了一些开源组件可能根本就没有办法去改。或者认为这个问题并不是这么严重，打个比方，扫出来是阻断的，开发觉得这个顶多算是一个主要问题，所以怎么去提升我们的权威性。于是，我们制定了一系列解决方案。首先我们会建立一个度量和可视化，然后每个月去跟进。最开始的话，这个技术债要求是不能超过10%，运行一段时间之后，要求不能超过5%，不能有新增的严重和阻断。然后成立语言专家小组。比如说开发如果对某一个规则提出置疑，那他可以把这个规则发给语言专家小组，语言专家小组会进行评审，评审通过之后组织级可以把这条规则下线，或者调整严重等级，比如是阻断的，可把它调成主要或次要。
![](/images/blog/devops-cmb-09.png)
制品仓库，这块的话因为我们有三个中心，有研发中心、数据中心、测试中心。每个中心都各自管理的，所以导致有一些术语会不统一。依赖仓库也是散落在各处。虽然说同是研发团队，同是开发者，但不同的开发室，会有各自不同的 maven 仓库。这一块对于组织级来说其实是不便于管理的。并且FTP没有唯一的标识。二进制制品形成多种多样。缺少同步和高可用方案。

所以这块我们是和 CMDB 配合统一了术语，然后与数据中心配合统一了制品的发布流程，用统一的工具管理各类制品。
![](/images/blog/devops-cmb-10.png)
大家可以看到这幅图，这个是我们制品库的样例图，第一个我们是用来管理我们的内部发布程序。就是开发人员编写了源代码，然后把源代码编译出二进制文件，流水线会自动把二进制文件上传到制品库去。  第二块是依赖包，像早前的话开发人员习惯性会把依赖包放到源码工具里面去，因为方便，依赖包跟源代码一起提交就可以了。但是现在我们是不允许这样做的，因为这样会导致源代码库非常大。我们说流水线我们要求快，如果代码库太大的话，就影响下载源代码的时间，它就没有办法做到快。所以我们现在是把这块依赖包剥离，放到制品库里面去。然后开发那边可以通过配置文件去调它的依赖库。另外一块是开源组件、中间件，这个是从第三方拿过来的，也是放在这里统一管理。我们走 docker 之后会有很多的基础镜像。现在基础镜像也会统一放在制品库里面，供开发去调用。然后开发也会打出一些应用的镜像，也会放在制品库里面。大家可以看到，在制品库里会有一些依赖定位的描述，比如说系统编号，发布单元版本。所以发布单元在我们这里是非常重要的。一个新系统过来，开发做的第一件事就是要规划他们的发布单元，发布单元是最小的管理单元，它是可以独立编译、独立部署的，但是不要求可以独立运行。
![](/images/blog/devops-cmb-11.png)
![](/images/blog/devops-cmb-11-1.png)
自动化部署的话，我们目前用的是 UCD，使用工具 UCD 定制部署流程。从制品库中自动获取发布包，按照预定义流程部署到目标环境。比如说 DEV 环境、ST 环境等。部署这块我们之前手工操作也是非常麻烦，并且我刚才提到了我们有测试中心、数据中心，比如说 UAT 测试，这个环境不是开发人员自己就可以下载安装包的。因为它是一个独立的环境，网段跟办公网是不通的，所以需要测试环境支持人员把这些包导到UAT测试环境上面去。生产环境也是，会需要数据中心的人，去把这个包导到生产环境上去。如果说当一天并发非常多的话，就需要排队，这样等待时间就长了，并且容易犯错，会影响部署时间和效率。我们之前走 CMMI，文档还是很全的，上线会有上线投产方案。对于部署的话，也会有安装说明书。安装说明书长，且无法保鲜。所以基本上每上一次线，可能都要把安装说明书重新写一下，因为可能有一些配置修改了。同时部署过程也是难以审计的，难以实现快速回滚。所以对于这块我们先是针对框架类的重点突破,比如基于 PaaS 平台的，然后针对高频发布类的应用重点突破。建立定期度量和可视化进展，查漏补缺。其实这一块推动起来还是比较容易的，因为开发切实感受到了效率的提升。

接下来给大家讲一下我们的自动化测试这块。自动化测试一直是我们努力的方向。今天像熊节老师也说了，DevOps 做得好不好关键看自动化测试。自动化测试这块，我们也做了一些尝试，也有了不小的进步，但关于覆盖率这块，可能还是需要进一步的摸索。自动化测试（比如接口测试）这块做得相对好一些，因为是由测试中心的同事去做的。单元测试是开发人员来做。开发人员会去衡量业务功能开发和工程实践的投入与产出，考虑他们所谓的“性价比”。
![](/images/blog/devops-cmb-12.png)
大家可以看到这个是常规的金字塔模型，越往下，回归成本越低，效率越高，缺陷也更容易定位。越往上更加接近业务，也反应真实的需求。这是比较推荐的一个自动化测试的模型。

大家可以看左上方的图，这个是我们早前的截图，是我们在用商业版工具的时候，当时就已经尝试做单元测试了，会把单元测试的报告集成到工具，方便集成人员查看。

右侧是我们自动化平台的一个截图，上面有显示测试案例多少，多少通过了自动化测试等等。现在的话，我们基本上把单元测试的结果是集成到 Sonar 上了，可以在 Sonar 上看测试覆盖率等一些相关的数据。另外我们做了非常多的度量报表，也会对单元测试有一些具体的统计。
![](/images/blog/devops-cmb-13.png)
自动化测试策略，主要分四个象限，上面两个是面向业务的，下面两个是面向技术的。左边的是结果可预期，右边的是结果不可预期。然后我们会根据产品所处的特定阶段，去选择要做哪些测试，谁去做。
![](/images/blog/devops-cmb-14.png)
这是分层自动化测试框架，第一个是测试冰淇淋型，大家可以看到手工测试是占比是最多的，然后是 UI、服务测试。第二种是测试金字塔型，单元测试占比是最多的，然后是服务测试接下去是UI测试。第三种是测试橄榄球型，服务测试是最多的，其次是单元测试和 UI 测试。在我们这边，用得最多的话是测试橄榄球型。因为我们精益敏捷类的现在是接口测试覆盖率要求达到100%，单元测试覆盖率还是希望能够根据开发的实际情况来定。如果是新系统研发，我们会要求单元测试作为故事的验收标准，也就是说必须要做的。UI自动化测试的话，因为投入成本比较高，所以只要求能够覆盖核心的场景就可以了。
![](/images/blog/devops-cmb-15.png)
在分层自动化测试这块，我们不要求遗留系统补单元测试。一般是针对新增的代码，要求写单元测试。组织级在推动过程中，会发现开发人员对自动化测试的动力不足。并且自动化测试的覆盖率要达到多少，这块也是需要我们不断去探索的，所以我们现在有一个团队，他们做 TDD 的，虽然说暂时没有发现明显的质量提升。但是他们还是愿意去做一些更深入的尝试。他们考虑把覆盖率再往上提，比方说提高到70%多、80%多。然后再去看一下质量、效能是不是有切实的改进。我们组织级也是想通过开发那边具体的实践，收集一些数据，一些正向反馈的数据，然后我们才在其他团队去做推广。目前我们这边也有团队在尝试用DDD的方法来重构老旧系统，这些都是很好的工程实践。

我们目前的分层自动化测试的策略是优先推行接口测试，鼓励单元测试。希望自动化测试，尽早的接入到持续交付流水线上去，变更触发或定时触发，每日至少跑一次。可以通过分层流水线，实现多级流水线的并行执行。建立持久的度量和反馈。
![](/images/blog/devops-cmb-16.png)
开源代码扫描，这块我们目前主要用的是黑鸭，主要是推荐 BSD、Apache、MIT 类的许可证。允许使用 MPL 类的许可证。谨慎使用 LGPL 类的许可证。不建议使用 GPL 类的许可证。
![](/images/blog/devops-cmb-17.png)
持续交付流水线是持续交付的核心实践。可以把上面说的各类实践串起来，可以串行或并行去跑。我们这边的流水线平台上支持创建各类模板，用户可以基于模板去创建流水线，也可以根据自己的需求去编排流水线的各个 STAGE，相当灵活。根据不同的分支策略，可以选择创建不同的流水线，单制品流水线或普通流水线或分层流水线。
![](/images/blog/devops-cmb-18.png)
我们都知道，代码检视对代码质量保障来说是至关重要的。所以我们这边还有一块实践就是代码检视，明年代码检视会是我们工作的一个重点。现在也在制定代码检视的一些规范和方法。代码检视方式目前主要分三种，一种是全体检视。这种方式便于知识的传播，因为每一个迭代团队大家一起检视，尤其对一些技术比较弱的，可以比较快的学到一些技能。第二种是通过PR的形式，通过合并请求，由技术骨干检视通过后代码才能交付到远程仓库，这种方式适用于异地协作模式，因为我们是三中心，三地的。尤其是近几年新员工较多，需要老员工把控下代码质量。第三种就是结对做代码检视，以旧带新。这种方式对新员工来说，提升会非常快。
![](/images/blog/devops-cmb-19.png)
这是我们内部的成熟度模型，成熟度分三级。一级包含了自动化编译、静态代码扫描、发布制品库三个工程实践。二级是在一级的基础上，增加了自动化部署。三级是在二级的基础上增加了单元测试和自动化测试。
![](/images/blog/devops-cmb-20.png)
这张图片上显示的一些度量指标，主要是我们的流水线的一些指标。构建效率，我们主要是看构建的耗时。构建次数、主要是看发布单元构建的次数。然后团队习惯主要是看是否用的主干开发，CI 频率是怎么样的，红灯的修复时间快不快。编译能力主要是看编译时间。测试完备性主要是看测试的覆盖率，测试类型覆盖。构建稳定性主要是看构建的成功率和异常构建率。其实我们现在并不是非常侧重于构建成功率，因为我们说持续集成的话，还是是欢迎大家试错的，我们现在更关注的是 MTTR，红灯修复时间。修复时间非常快，说明问题很快得到了解决，大家可以继续往该分支上提交代码。

在编译时间这一块，我们建议不要超过15分钟，这个时长可以不包括自动化测试，比方说接口测试、集成测试和 UI 测试，包含单元测试。尤其是 UI 测试，执行时间还是比较长的，所以这个时候我们会建议用户去建分层流水线，分层流水线可以固定放在晚上去跑，第二天查看结果。
![](/images/blog/devops-cmb-21.png)
这张是杭州中心的月报图，上面会有各种关键度量数据，趋势图。我们每月发布一版，供团队和领导参考。
![](/images/blog/devops-cmb-22.png)
最后是我们 DevOps 标准认证评估分享环节。先做一个概况介绍，我们都知道招行是第一批参加 DevOps 标准认证评估的。我们在2018年的时候，就有4个项目，财富 W+，招赢通、基金、排队机4个项目通过了标准3.0的评估。今年领导也非常鼓励我们继续去参评，主要也是为了驱动内部的一些工程实践能够更好的落地。所以今年是要求精益敏捷产品，运作一年以上的，分5批参与评估，目前已经进行到了第4批。持续交付标准一共涉及7个过程域，49个评估项。我们在评估之前，会把各个参评团队的数据、情况都收集上来。然后跟依次跟这49个评估项去做比对。主要是看三级、四级、五级的能力，看差距在哪里。对于一些能够快速改进的，就马上进行整改。所以整体优化下来，对我们的推动还是蛮大的。同时，我们会发现，开发人员的潜力是巨大的。能够在短时间内掌握各种单测框架，并能快速提升自动化测试覆盖率。
![](/images/blog/devops-cmb-24.png)
从结果看，不是说开发不会写单元测试，而是他们可能更倾向于去做一些业务上的开发，所以 DevOps 标准认证对我们的推动，自动化测试这块，尤其是单元测试，我认为提升还是非常明显的。我们之前有一个试点团队，2016年开始转型敏捷，之前也有借助外部的咨询师来给他们做咨询，比方说要不要做单元测试，怎么去做，但是他们也有自己的考量，因为业务那边压得特别紧，业务希望每个迭代能产出更多的功能，而并不关注工程实践做得有多好，代码质量有多高，所以他们之前也尝试做了自动化单元测试工具，想借助自动化单元测试工具自动生成单元测试脚本、用例，但因为种种原因一直没有落地。但通过这次外评，他们很快就把单元测试做起来了，并且覆盖率还挺高。另一块就是通过外评，帮助我们找到了工具链的改进方向，目前是两周一个迭代持续优化。举个例子，评估前源代码管理工具码云上并没有代码评审这个功能，外评后，我们在上面做了代码评审的功能，并且跟 tracker 做了联动。检视出来的代码质量问题，可以直接记录在码云上，同时会同步到 tracker 对应的故事卡片上，然后可以持续跟进。流水线平台上也是，评估后，我们增加了安全扫描等，所以这块对我们推动还是比较大的。让我们知道哪些做得是比较领先的，哪些是还有改进空间的。

##### 互动问答

- **互动一**：

**提问1**：请问，咱们招行做这个4个项目，然后我想了解在招行内部，开发、测试、运维是三个部门，还是说我们也是开发、测试、运维完全在一个团队里？

**滕乐英**：我们是三个中心，三个中心是分开的，不是在一个团队里面。

**提问**：那在做认证的时候，其实三方的协作会非常多在这方面有没有遇到一些阻碍或者困扰？

**滕乐英**：其实还好，因为我们现在已经平台化、工具化了。很多实践都是通过流水线去跑的，并且我们有度量平台，可以用数据说话。我们内部也有技术教练，不同技能的技术教练会负责跟进不同的问题。最关键的是，大家都比较重视，所以总体来说还好。

**提问**：您刚才展示的工具确实特别多，我想知道这些工具是完全做到端到端打通了还是说工具之间其实还是孤岛，有没有哪一项是孤岛存在的？

**滕乐英**：工具和工具之间有 API，相互之间可以调用。我们后续计划是起个项目，会把这些工具全部整合到一个平台上去，这是我们明年计划做的事情。

**提问**：需求管理，用的是 tracker么？

**滕乐英**：需求管理，其实分两块，因为我们行内是双模的，有传统的，有走精益敏捷的，所以需求管理，传统项目的是放在 VP 里面，精益敏捷的是放在刚才介绍的 tracker 上，这是我们自己分装的一个工具。

**提问**：认证的4个项目，全是基于敏捷，还是说也有您刚才说的传统的也有？

**滕乐英**：参评的全部是走敏捷的，传统的不参评。

- **互动二**：

**提问2**：请问，刚才你讲的测试，好像没有涉及到 UI 自动化测试？

**滕乐英**：有涉及的，我们 UI 自动化测试，会侧重于测核心的一些场景。

**提问**：工具用的是什么？

**滕乐英**：主要用 Robot Framework，通用模拟器。

- **互动三**：

**提问3**：请问，在测试数据管理方面，有没有实践？

**滕乐英**：测试数据管理，一块是生产数据脱敏，有些数据还是比较难脱敏的。所以另外一块是通过工具自动造数，很多团队都会用工具去自动造数。

**提问**：你们内部有这样的工具吗？

**滕乐英**：对，我们内部有这样的工具。

**提问**：大概是什么原理，可以简单介绍一下吗？

**滕乐英**：开发、测试人员会编写一些脚本自动化生成测试数据。

**提问**：有一些数据是测试人员自己造的？

**滕乐英**：是的，测试人员会造数。

--------

#### 关于作者
<center>
![](/images/blog/devops-cmb-author.webp" />

滕乐英

招商银行

杭州研发中心

DevOps 推广负责人&技术教练
</center>

在招商银行工作14年，由开发转型做配置管理、DevOps，参与招行 DevOps 持续交付流水线平台的建设、推广，及 DevOps 标准认证评估工作。目前主要负责杭州研发中心及分行的 DevOps 持续交付实施与推广，并兼任行内精益技术教练一职。