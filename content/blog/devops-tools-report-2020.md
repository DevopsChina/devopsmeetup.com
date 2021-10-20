---
title: "2020年DevOps工具报告"
date: 2020-07-23T11:36:56+08:00
description: "虽然在过去的几十年里，许多软件方法论已经渐渐落伍，但很显然，DevOps并不是一种趋势，它正在成为软件开发和运营的标准方式。如今，企业团队正处于DevOps转型的不同阶段，努力实现更快、更安全的技术交付，以获得竞争优势。"
bgImage: "images/backgrounds/blog-bg.jpg"
bgImageAlt: "ALT-txt"
image: "images/blog/devops-tools-report-2020-000.png"
author: "吴平福 周一行 付文新"
postType: "翻译"
type: "post"
summary: "虽然在过去的几十年里，许多软件方法论已经渐渐落伍，但很显然，DevOps并不是一种趋势，它正在成为软件开发和运营的标准方式。如今，企业团队正处于DevOps转型的不同阶段，努力实现更快、更安全的技术交付，以获得竞争优势。"
categories: 
  - "翻译"
tags:
  - "DevOps"
---


>社区译者：吴平福 周一行 付文新   
审校：王立杰 王英伟 高俊宁 陈文峰   
原作者：GitKraken          
<!-- 原文地址：[https://martinfowler.com/articles/continuousIntegration.html](https://martinfowler.com/articles/continuousIntegration.html)    -->

### 摘要

虽然在过去的几十年里，许多软件方法论已经渐渐落伍，但很显然，DevOps并不是一种趋势，它正在成为软件开发和运营的标准方式。如今，企业团队正处于DevOps转型的不同阶段，努力实现更快、更安全的技术交付，以获得竞争优势。 
当开发人员与IT领导协同工作，消除路障，创建一个无缝的软件开发生命周期时，对组织的生产力、绩效、可视性、协作和创新都会产生不可思议的效果。 

也就是说，向DevOps过渡并不容易，也不直接。它需要重大的改变，包括：进化员工的思维方式，引入合适的工具，以及教授新的技能。无论你的DevOps转型在哪个阶段，你的重点都应该是持续改进。从基础开始，然后确定你独特的制约因素；一旦这些制约因素不再阻碍你，就重复这个过程。 

没有合适的工具是一个相当容易消除的制约因素，也值得投资。本报告的任务是提供指导，并从已经成功实施DevOps工具的开拓者那里获得最佳的DevOps工具。我们询问了全球的开发者社区，他们依靠哪些工具来实现DevOps的成功，我们很荣幸地提交这份报告，这份报告是基于2700多条回复的结果。


### 主要研究结果

当谈到工具时，有用和易用的工具是消费者所期望的，但技术专家们往往认为，由于他们的专业知识，他们可以使任何工具发挥作用。实际上，事实恰恰相反：由于构建复杂系统和管理关键业务基础设施的困难程度，好的工具更重要。 

**"表现最好的⼯程师拥有易⽤⼯具的可能性是普通⼯程师的1.5倍。" - DORA & Google Cloud发布的2019年DevOps状况报告**

在DevOps转型过程中，开发团队被授权对工具做出自己的决定，有助于提高软件交付绩效。他们还将工具自动化并集成到工具链中，从而腾出时间用于新的开发，并驳斥了那些认为实施起来太过耗时或昂贵的说法。

<!-- ![](/images/blog/devops-tools-report-2020-001.png ) -->

### 计划

#### 项目管理和问题跟踪

##### 主要研究结果

无论你的团队是使用Scrum、Kanban还是敏捷项目管理的混合方法，你很可能已经做了很长时间的问题跟踪。项目管理和问题跟踪是DevOps计划过程的基础，当团队合作时，这些工具可以提供有价值的透明度、问责制和计划的准确性。 

集成和自动化在这个领域越来越重要，可以减少上下文切换，并提供跨平台执行和跟踪任务的能力。高绩效的技术团队经常将Slack和GitHub等工具集成到他们的问题跟踪流程中。

##### 工具

<!-- ![](/images/blog/devops-tools-report-2020-002.png ) -->

[JIRA](https://www.atlassian.com/software/jira) - Jira是一个Atlassian工具，最初是作为Bug和问题跟踪器设计的。如今，Jira已经发展成为一个强大的工作管理工具，适用于各种用例，从需求和测试用例管理到敏捷软件开发。

Jira提供了规划和路线图工具，因此团队可以管理利益相关者、预算和功能需求。Jira集成了各种CI/CD工具，以促进整个软件开发生命周期的透明度。当需要部署的时候，实时的生产代码状态信息会在Jira问题中浮现出来。集成的功能标记工具允许团队逐步、安全地推出新功能。

这是一个受欢迎的DevOps计划工具，因为它包括：发布和冲刺计划、CI/CD集成、问题管理、项目待办列表、功能标记、Jira服务台集成、以及其他开发者工具集成。它的可配置性很强，这对于复杂的项目管理来说是很好的，但如果你想找一个易于实施和维护的系统，它可能不是最好的选择。

![](/images/blog/devops-tools-report-2020-003.png )

<!-- ![](/images/blog/devops-tools-report-2020-004.png ) -->

[Trello](https://trello.com/en-US) - Trello是一个项目管理工具，将项目组织成看板式的板子。2017年，Trello被Atlassian收购，此后，Trello作为Jira的轻量级替代方案，在软件开发团队中获得了很大的吸引力。如果你的组织还不是已经依赖Jira，你可以考虑使用Trello。它更容易配置和管理，而且通常情况下，开发人员更愿意与之对接，而不是Jira，由于所有的自定义功能，Jira可能会变得相当复杂，有时也会变得笨重。

Trello提供了Web和移动版本。你的项目板会告诉你正在做什么，由谁来做，以及在一个过程中处于什么位置。项目板上写满了卡片，这些卡片是你和你的团队的任务。你的团队可以对卡片进行评论和协作，每个卡片上都可以有照片、附件、截止日期等。

要想从Trello中获得更多的收益，你可以通过Power-Ups与其他开发工具如Slack和GitHub集成。

![](/images/blog/devops-tools-report-2020-005.png )

<!-- ![](/images/blog/devops-tools-report-2020-006.png ) -->

[Glo Issue Boards](https://gitkraken.com/glo) - Glo Issue Boards是在GitKraken工具套件中的由Axosoft开发的产品。如果你不熟悉的话，它与Trello类似，但Glo更以开发者为中心。这个任务和问题跟踪系统允许开发团队在看板、日历、时间线或仪表板中可视化任务。

Glo直接与GitHub集成，以减少开发团队在完成任务时的上下文切换。Glo与GitHub的问题和里程碑进行双向实时同步，因此开发人员和管理人员可以随时了解当前项目的进展情况。 

高绩效的开发人员依靠自动化来提高工作效率，而赋予自动化功能的计划/跟踪工具正是基于这个原因而变得非常强大。使用GitHub Actions很容易设置Glo卡自动化，以减少开发人员工作流中的步骤数：本质上是通过工作流实现任务的自动化进程。 

此外，将卡与拉动请求链接起来，可以进一步实现自动化。当GitHub中的拉动请求状态被更新时，Glo卡会根据你选择的映射自动推进到另一列。Glo与GitKraken Git GUI完全集成，因此开发者在GitKraken中创建GitHub的拉取请求时，可以实际链接一个Glo卡。这些自动化功能非常符合DevOps策略，可以减少上下文切换，提高效率。

![](/images/blog/devops-tools-report-2020-007.png )

<!-- ![](/images/blog/devops-tools-report-2020-008.png ) -->

[GitKraken Timelines](https://gitkraken.com/timelines) - GitKraken Timelines是Axosoft的一个产品，它是Axosoft在GitKraken 工具套件。它旨在帮助团队以时间轴视图的形式规划和沟通项目目标和里程碑。对于高层规划来说，这是一个很好的工具，可以快速传达即将到来的最后期限或回顾进度。每个里程碑都可以有一个图片或GIF以及相关的子项目。很容易叠加多个时间轴来比较不同项目或团队之间的截止日期。时间轴可以是私有的、协作的或公开的。而且它们可以通过链接、嵌入或演示模式轻松共享。 

当你开始进行DevOps转型时，考虑创建时间轴来清楚地传达主要的里程碑，每个里程碑需要完成哪些任务，以及相关的最后期限是什么。这个规划工具可以让每个人都朝着同一个目标前进。

![](/images/blog/devops-tools-report-2020-009.png )

<!-- ![](/images/blog/devops-tools-report-2020-010.png ) -->


### 代码

#### 版本控制

##### 主要研究结果

版本控制是一种跟踪和管理代码修改的方法；允许开发人员看到项目的完整修改历史，并在需要时返回到以前的版本或文件。全球范围内的团队正在摆脱集中式版本控制系统（VCS），如Subversion，转而迁移到Git。根据Stack Overflow的开发者调查，由于Git是一种免费的分布式VCS，利用了分支和合并功能，现在超过90%的开发者都在使用Git进行版本控制。 

#### 托管服务

##### 主要研究结果

为了使用Git进行项目协作，你需要一个托管服务来托管你的存储库；另外，有些企业会选择将其托管在内部服务器上，以更好地满足其安全或部署需求。在决定使用哪种托管服务时，你的企业需要考虑价格、存储容量、与现有工具的集成度等等。企业团队将其存储库托管在多个服务上的情况也不少见。

##### 工具

<!-- ![](/images/blog/devops-tools-report-2020-011.png ) -->

[GitHub](https://github.com/about)  - GitHub的核心部分，是一个托管和审核数以亿计的私有、公共和开放源码仓库的平台。GitHub也是构建该产品的公司的名字，它在2018年被微软收购。在我们的DevOps报告中，GitHub不仅在托管服务中排名第一，在我们的2020年20大开发者工具报告中，GitHub排名第7位。

![](/images/blog/devops-tools-report-2020-012.png )

GitHub正在不断扩展其产品，以配合DevOps工作流程中越来越多的流程。为了与GitHub存储库对接，许多开发者使用GitKraken Git GUI，它与GitHub.com和GitHub Enterprise无缝集成。GitHub提供了项目（Project）和问题（Issues）的基本项目管理。像Glo Issue Boards这样的工具提供了与GitHub同步的集成，可以提供更强大的计划和跟踪功能。GitHub的其他核心组件包括代码审核、安全开发，以及最近的CI/CD。

<!-- ![](/images/blog/devops-tools-report-2020-013.png ) -->

[Bitbucket](https://bitbucket.org/product)  - Bitbucket是Atlassian的产品，首先是一个代码管理工具。为了与托管在Bitbucket上的Git repos对接，GitKraken的GUI和其他几个Git客户端与Bitbucket.org或Bitbucket Server集成，提供了一个精简的工作流程。

遵循DevOps的方法论，Bitbucket已经将其提供的服务扩展到不仅仅是托管，还包括项目规划、协作、测试和部署服务。正如你所期望的那样，Bitbucket提供了与Jira的紧密集成，Trello也有了与Bitbucket Cloud集成的Powerup。

![](/images/blog/devops-tools-report-2020-014.png )

<!-- ![](/images/blog/devops-tools-report-2020-015.png ) -->

[GitLab](https://about.gitlab.com/stages-devops-lifecycle/source-code-management/) -GitLab
在我们的DevOps报告中，GitLab是最常用的托管服务的第3位，也是最受欢迎的托管服务。

#2020年Top 20开发者工具排行榜中的第14位。GitLab是最早全面拥抱DevOps的托管服务之一，此后一直致力于打造一个完整的DevOps平台。GitLab提供了管理、计划、创建、验证、打包、发布、配置、监控和安全应用的一切。为了进一步简化开发工作流程，可以利用GitKraken的GUI与GitLab.com和GitLab Self-Managed上的Git仓库进行集成。

![](/images/blog/devops-tools-report-2020-016.png )

<!-- ![](/images/blog/devops-tools-report-2020-017.png ) -->

[Azure DevOps](https://azure.microsoft.com/en-us/services/devops/repos/) -Azure DevOps是微软的一款产品，提供Git仓库托管、报告、需求管理、项目管理、自动构建、实验室管理、测试和发布管理功能。该产品于2018年发布，取代了Visual Studio Team Services (VSTS)等工具，并结合了许多其他工具，覆盖了整个应用生命周期，实现了DevOps功能。要扩展您的DevOps工具链并进一步简化开发，请将GitKraken Git GUI与您的Azure DevOps托管的Git仓库集成。

![](/images/blog/devops-tools-report-2020-018.png )

#### 源码管理客户端

##### 主要研究结果

源代码管理（SCM）系统是帮助团队和开发人员跟踪项目历史的工具。一个Git GUI（图形用户界面）将Git中发生的事情转换成一个你的眼睛和大脑都能很容易理解的界面。

GUIs提供了一个至关重要的清晰的视觉展现层，消除了CLI的黑匣子体验。GUIs还通过用简单的拖放操作代替记忆命令列表的需要，减少了Git的陡峭的学习曲线。在操作上，GitKraken Git GUI比CLI更快、更高效，比如以下操作任务：身份验证、克隆repo、查看提交图、查看远程URLs、查看文件差异、将更改从本地repo推送到远程、访问文件历史记录和错误、执行Pull Request和合并解决方案，以及执行一个交互式的rebase操作。

没有Git GUI，企业很难在所有开发团队中标准化和扩展Git的使用。GitKraken Git GUI的持续增长说明了为什么GUI方法对于用Git实现成功的DevOps工作流是不可或缺的。

##### 工具

<!-- ![](/images/blog/devops-tools-report-2020-019.png ) -->

[GitKraken](https://www.gitkraken.com/git-client) Git GUI-连续四年被评为“开发者工具”的第一名，GitKraken Git GUI是由Axosoft构建的GitKraken工具套件中的旗舰产品。它允许开发人员在彩色图形中可视化Git存储库的历史，并将复杂的Git命令简化为拖放操作。通过内置的合并冲突编辑器、交互式rebase模式、内置的代码编辑器、集成工具等，GitKraken Git GUI为有经验的开发人员简化了的Git工作流，并减少了刚接触Git的人员的陡峭的学习曲线。

GitKraken在其他客户端中脱颖而出，因为它是兼容Linux、Mac和Windows的为数不多的GUI之一，而GitHub Desktop和Sourcetree不支持Linux。它在DevOps工作流中扮演着关键的角色，它紧密地连接了各种代码工具：Git客户端、托管服务和IDE（它使用了VS Code内置的Monaco代码编辑器）。
GitKraken Git GUI集成了上一节中列出的所有顶级的Git托管服务：GitHub、GitLab、Bitbucket和Azure DevOps，以及它们的自托管服务（不包括TFS），可以从GitKraken内部实现以下所有功能：在托管帐户上创建存储库，包括.gitignore文件和license文件；自动生成一个SSH密钥对，并将其添加完成；fork存储库；将身份验证保存到配置文件中；从您的repo列表中克隆；为repo添加远程地址；使用添加的分配者、审阅者和标签创建pull requests；查看pull requests的构建状态。

GitKraken Git GUI还通过连接计划和代码步骤，支持无缝的DevOps工作流。GitKraken Git GUI内置了Glo Issue Boards和GitKraken Timelines等规划工具。为了便于跟踪，Git GUI中的存储库可以与Glo Boards相关联。当创建一个新的GitHub pull request时，只需链接一个Glo card；这将自动更新GitHub中的pull request描述，以包含到该卡的链接。另外，GitKraken Git GUI与Glo Issue Boards、Jira、GitHub Issues和GitLab Issues的更紧密、更强大的集成版本即将推出！

![](/images/blog/devops-tools-report-2020-020.png )

<!-- ![](/images/blog/devops-tools-report-2020-021.png ) -->

[Git CLI](https://git-scm.com/book/en/v2/Getting-Started-The-Command-Line)-在Git GUI之前，程序员被迫使用命令行界面（CLI）。CLI继续被广泛使用，因为它是免费的，许多人仍然通过记忆命令来学习Git。此外，它还提供了额外的好处，即能够使用脚本自动执行某些任务。一些开发人员也不希望依赖于GUI应用程序，而是希望看到他们输入的命令的输出。

![](/images/blog/devops-tools-report-2020-022.png )

<!-- ![](/images/blog/devops-tools-report-2020-023.png ) -->

[GitHub Desktop](https://desktop.github.com/)-顾名思义，GitHub Desktop是一个GitHub工具，在微软旗下。由于GitHub.com拥有广泛的用户群，该工具已被广泛采用。对于GitHub用户来说，它是一个免费的、易于使用的工具，但是它的功能不如GitKraken Git GUI或Sourcetree那么强大。对于那些不使用GitHub作为托管服务的，或使用多个托管服务的人来说，GitLab、Bitbucket或Azure DevOps没有集成其中，这是一个相当重要的工作流的障碍。

GitHub Desktop非常适合已经使用GitHub.com并且需要基本Git客户端功能的Windows和Mac开发人员，例如：与协作者一起分配提交；使用pull request检出分支，并查看CI状态；语法突出显示的差异；扩展的镜像差异支持。Git客户端不适用于Linux用户或团队，这些用户或团队需要一个客户端来进行：交互式rebase、提交签名、GitFlow、子模块、blame、打开多个repo、自动存储、提交模板、文件/差异视图、文件编辑等。GitHub Desktop也没有提交图，因此可视化项目历史的能力有限。

![](/images/blog/devops-tools-report-2020-024.png )

<!-- ![](/images/blog/devops-tools-report-2020-025.png ) -->

[Sourcetree](https://www.sourcetreeapp.com/)-Sourcetree是Atlassian产品，2010年首次向公众发布。这个Git客户端对Windows和Mac是免费的，但不支持Linux。作为市场上最早的Git GUIs之一，Sourcetree能够在开发人员中获得巨大的吸引力，特别是那些已经使用了类似Jira和Bitbucket的Atlassian产品的开发人员。

Sourcetree的功能比GitHub桌面丰富得多，与GitKraken Git GUI的功能更接近。然而，Sourcetree缺少模糊查找器、语法突出显示、自动存储、文件/差异视图、文件编辑和pull request模板。

说到DevOps，Sourcetree提供了与GitHub、GitLab和Azure DevOps的集成，主要对手是Bitbucket。

![](/images/blog/devops-tools-report-2020-026.png )

#### 集成开发环境

##### 主要研究结果

由于IDEs提供的便利性，它们越来越受到软件开发人员的欢迎。IDE是一个软件套件，它将开发人员用来编写和测试软件的许多工具整合到一个用户界面中。IDEs提供了较少上下文切换的优势，这就是为什么许多工具都朝着这个方向发展，比如：GitKraken Git GUI及其内置的代码编辑器、合并冲突工具和集成的问题跟踪功能。

##### 工具

<!-- ![](/images/blog/devops-tools-report-2020-027.png ) -->

[VS Code](https://code.visualstudio.com/)-VS Code不仅是我们DevOps报告中排名第一位的IDE，而且在2020年、2019年和2018年的20个顶尖开发工具中，它还排名第二位。VS Code是一个非常流行的代码编辑器，用于在Windows、Mac和Linux上编写、构建和调试web和云应用程序。

作为微软公司的工具，它还具有与Azure、AWS、.NET紧密集成的额外优势，以及一个庞大的插件的生态系统，允许您连接、构建和调试许多工具和技术。通过VS Code与Azure一起使用可以简化DevOps工作流，以便轻松部署和托管基于React、Angular、Vue、Node、Python等构建的站点。此外，使用VS Code的Glo Issue Boards插件，可以加快任务和问题跟踪。

![](/images/blog/devops-tools-report-2020-028.png )

<!-- ![](/images/blog/devops-tools-report-2020-029.png ) -->

[IntelliJ IDEA](https://www.jetbrains.com/idea/)- IntelliJ IDEA是Jetbrains提供的Java开发IDE，它创建了一整套开发工具。虽然IntelliJ没有VS Code那么流行，但它是DevOps报告中使用最多的IDE的第二位，也是2020年的前20个最好的开发工具中的第9位。该开发工具的吸引力逐年上升，在我们的20大开发工具报告中，2019年排名第10位，2018年排名第11位。

IntelliJ IDEA作为编程软件，提供了快速直观的体验。虽然IntelliJ是一个用于Java的IDE，但它也理解并为其他各种语言，比如：SQL、JPQL、HTML、JavaScript等，提供智能编码帮助。

为了增强DevOps工作流，IntelliJ IDEA支持Maven、Gradle、Ant、Gant等构建工具，以帮助自动化编译、打包、运行测试、部署和其他活动。为了方便地执行单元测试，IntelliJ包含了主要测试框架的测试运行程序和覆盖工具，包括JUnit、TestNG、Spock等。此外，IntelliJ IDEA还提供了一个专用的工具窗口，允许您连接到本地运行的Docker来管理镜像、容器和Docker Compose服务。

![](/images/blog/devops-tools-report-2020-030.png )

<!-- ![](/images/blog/devops-tools-report-2020-031.png ) -->

[Visual Studio](https://visualstudio.microsoft.com/vs/)-Visual Studio是微软开发的另一个IDE，不要与Visual Studio Code（VS Code）混淆。它也很受欢迎，在我们的DevOps报告中排名第三，在2020年的前20个开发工具中排名第四。这个集成开发环境包括所有平台和语言的工具和服务。

Visual Studio提供了一些特性来帮助处理DevOps工作流的各个部分：开发、分析、调试、测试、协作和部署。此外，作为一个微软工具，Visual Studio通过Azure的项目模板和直接部署到Azure，使Azure开发更加容易。另外，Visual Studio还有一个扩展市场，可以与其他流行的开发工具集成。

![](/images/blog/devops-tools-report-2020-032.png )

<!-- ![](/images/blog/devops-tools-report-2020-033.png ) -->

[Sublime Text](https://www.sublimetext.com/)-Sublime Text是一个跨平台的文本编辑器，用于代码、标记和文本。这个成熟的IDE是稳定和快速的。它具有自动完成、语法突出显示和代码折叠功能。Sublime Text是DevOps报告中使用最多的第4个IDE，也是2020年前20个开发工具中使用最多的第8个IDE。

![](/images/blog/devops-tools-report-2020-034.png )

<!-- ![](/images/blog/devops-tools-report-2020-035.png ) -->

### 构建

#### 构建工具

<!-- ![](/images/blog/devops-tools-report-2020-036.png ) -->

[Jenkins](https://jenkins.io/)-Jenkins是一个开源的自动化服务器，允许组织通过自动化来加速他们的软件开发。Jenkins在整个DevOps生命周期中管理和控制软件交付过程，包括构建、测试、运维和部署。设置Jenkins以监视GitHub、Bitbucket或GitLab上的任何代码更改，并使用Maven和Gradle等工具自动进行构建。利用容器技术，如Docker和Kubernetes，启动测试，然后在生产中采取回滚或前滚等操作。

<!-- ![](/images/blog/devops-tools-report-2020-037.png ) -->

[Maven](https://maven.apache.org/)-Maven是一个构建自动化工具，主要用于Java项目，但也可以用于构建和管理用C#、Ruby、Scala和其他语言编写的项目。Maven项目由Apache软件基金会托管。

团队可以使用Maven的项目对象模型（project object model，POM）和一组插件，来使用统一的构建系统构建项目。一旦您的团队熟悉了一个Maven项目是如何构建的，您就会知道所有Maven项目是如何构建的，从而在尝试确定许多项目时节省了时间。

<!-- ![](/images/blog/devops-tools-report-2020-038.png ) -->

[Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/compiling-and-building-in-visual-studio?view=vs-2019)-Visual Studio的Windows和Mac版本有用于所有.NET语言的内置编译器工具。使用它可以立即创建构建，并在调试器中测试它们；为C++和C类项目运行多处理器构建；自定义构建系统的不同方面。您可以使用MSBuild命令行工具来自动化Ci/CD管道中的构建，或者在Windows和Linux中使用CMake工具运行C++构建。

<!-- ![](/images/blog/devops-tools-report-2020-039.png ) -->

[Gradle](https://gradle.org/)-Gradle是一个开源的构建自动化系统，可以帮助团队更快地构建、自动化和交付更好的软件。开发人员可以使用Gradle来编写Java、C++、Python等，并在任何平台上打包部署。Gradle的插件和集成生态系统帮助团队扩展自动化。端到端地对软件的交付进行建模、集成和系统化，并使用快速构建扩展开发。Gradle提供了许多功能，从编译避免到高级缓存，再到支持持续交付。

![](/images/blog/devops-tools-report-2020-040.png )

### 测试

#### 执行测试

##### 主要研究结果

测试框架对于成功的DevOps策略是不可或缺的，因为它们有助于为创建和设计测试用例提供高级指导。测试框架提供了实践和工具的组合，旨在帮助开发和QA团队更有效地测试。

测试工具可以帮助企业团队提高测试速度、提高准确性、降低维护成本和降低出错风险。有了高效的DevOps工作流，开发人员可以在持续交付期间使用这些工具，来减少QA的监督。

##### 工具

<!-- ![](/images/blog/devops-tools-report-2020-041.png ) -->

[JUnit](https://junit.org/junit5/)-JUnit是一个面向Java的开源单元测试框架。JUnit对于在测试驱动环境中工作的开发人员非常有用，因为它有助于在代码的早期发现错误，从而使代码更加可靠。单元测试还迫使开发人员花更多的时间阅读代码而不是编写代码。这会产生更可读、更可靠、无错误的代码，从而在开发过程中建立信心。

![](/images/blog/devops-tools-report-2020-042.png )

<!-- ![](/images/blog/devops-tools-report-2020-043.png ) -->

[Selenium](https://www.selenium.dev/)-Selenium是一套自动化web浏览器的工具。它提供了一个回放工具，用于编写功能测试，而无需学习测试脚本语言。

Selenium WebDriver是特定语⾔言绑定的集合，用于驱动浏览器。它帮助QA团队创建健壮的、基于浏览器的回归自动化套件和测试，并可以跨许多环境扩展/分发脚本。

Selenium IDE是一个Chrome和Firefox插件，可以简单地记录和回放与浏览器的交互。它帮助QA团队创建快速的bug复制脚本，以及用于自动化辅助的探索性测试脚本。

Selenium Grid非常适合希望通过在多台机器上分发和运行测试来扩展规模的QA团队，同时从一个中心点管理多个环境。这使得在各种浏览器和操作系统上运行测试变得很容易。

![](/images/blog/devops-tools-report-2020-044.png )

<!-- ![](/images/blog/devops-tools-report-2020-045.png ) -->

[Jest](https://jestjs.io/)-Jest是一个JavaScript测试框架，可以与Babel、TypeScript、Node、React、Angular和Vue一起工作。Jest速度快，几乎不需要配置。它使用快照测试来跟踪大型对象；快照可以与测试一起运行，也可以嵌入代码。

![](/images/blog/devops-tools-report-2020-046.png )

<!-- ![](/images/blog/devops-tools-report-2020-047.png ) -->

[PHPUnit](https://phpunit.de/)-PHPUnit是一个面向程序员的PHP测试框架。它是单元测试框架的xUnit架构的一个实例。许多现代PHP框架都带有PHPUnit集成，包括Laravel、Symfony和CakePHP。CMS包括Wordpress和Drupal也使用它进行测试。
 

### 发布

#### 配置管理

Ansible - Ansible为基础设施、应用、网络、容器、安全乃至更多其他多样性的系统提供了简单的自动化方案。Ansible通过配置对基础设施的数据信息进行直接描述，提升了文档的可读性。系统管理除了账号密码或者SSH密钥外，再也无需它物。不需要再安装代理软件，避免了自动化系统常见的“为了管理而管理代理软件”的问题。Ansible依赖于OpenSSH，而它又是最安全的远程配置管理系统之一。

Ansible不仅在DevOps报告中位列配置管理工具第一名，而且在2019年Stack Overflow的开发者调查显示：62%的使用过Ansible的开发者都特别喜欢这个工具。
 
![](/images/blog/devops-tools-report-2020-048.png )

Azure DevOps -Azure DevOps是由微软创建的一系列DevOps解决方案的集合。使用Azure云的自动化功能简化了其中的配置管理。整个系统的资源配置的统一管理增强了系统状态的可靠性，做到随时回滚配置更新，自动化处理异常修改和问题排查。

编辑和管理PowerShell的配置，导入配置脚本，生成节点配置，这些都可以在云上完成。使用Azure配置管理来监测和自动化更新物理机和虚拟机的配置。

![](/images/blog/devops-tools-report-2020-049.png )

Chef-Chef 是一个处理物理机、虚拟机和云上主机的配置管理工具。它赋能IT流程的持续自动化，促进企业组织的高效团队协作，Chef Automate利用chef、Habitat和InSpec构建横跨内外边界的管道，标准化本地数据中心和公有云的环境和流程。

DevOps人员利用相同的工具把配置编程代码，流程化处理申请，高效的准备环境和发布应用。

![](/images/blog/devops-tools-report-2020-050.png )
 

#### 持续集成/交付（CI/CD）

##### 主要研究结果

持续集成是DevOps最佳实践之一，旨在一天多次合并代码到同一个共享库，然后从此库开展自动化构建和测试。CI助力于企业研发小组快速监测错误，减少合并错误，避免问题积压恶化。

持续交付在CI之上更进一步，使得软件可以在任意时间内发布到生产环境，通常自动化推送更新到临时系统中。企业研发小组认为DevOps的CD实践保证了每次的修改都能发布，而且还降低了每次发布的风险。这让企业通过更频繁的提供价值获得竞争优势，创建更为紧密的客户反馈闭环。

#### 工具

[Jenkins](https://jenkins.io/) - Jenkins 是我们调研报告中排名第一的CI/CD工具；它有助于企业通过自动化加速软件开发。Jenkins通过DevOps生命周期控制和管理着整个软件的交付周期，包括：构建、测试、运维和部署。通过Jenkins来监控GitHub、Bitbucket 或者GitLab中的任何代码变化，并自动触发利用Maven或者Gradle编译的构建。利用如Docker和Kubernetes的容器技术初始化测试环境，并在生产环境中进行回滚或前滚。

[GitLab](https://about.gitlab.com/) - GitLab通过自行演进，成为了一个覆盖整个DevOps周期的应用。因此GitLab CI/CD只是整个GitLab应用中的一小部分，提供从计划到部署的无缝用户体验。可以利用GitLab CI/CD在Unix、windows、macOS或者任何运行Go语言的环境，此外还支持多机器构建，以加快速度执行速度。GitLab CI/CD还支持实时日志输出、柔性pipeline和可视化pipeline、自动拓展、制品构建、支持Docker和容器注册等等。

[Azure DevOps](https://azure.microsoft.com/en-us/services/devops/repos/) - Azure DevOps是由微软创建的一系列DevOps解决方案的集合。开发人员利用它可以自动化从编码到上云的整个持续集成和持续交付的DevOps流程。

通过Azure的端到端的解决方案，开发团队可以实现整个应用生命周期(计划、开发、交付和运维)内任何阶段内的DevOps实践。通过与Visual Studio和VS Code的紧密集成，开发者更容易在Azure DevOps上致力于自己的CI/CD流水线。

[Travis CI](https://www.travis-ci.org/) - Travis CI是由Github提供的持续集成服务，用于构建和测试上传在它上面的工程。相较于Jenkins，使用Travis CI的一大优势是更快的初始化：登录GitHub、测试工程、推送至GitHub一气呵成。如果你所在的组织利用Github开展开源项目，Travis CI是一个好选项。Travis CI还集成了广受欢迎的通讯工具，例如Slack，以保证开发团队随时了解构建状态。
 
### 部署

#### 部署环境

##### 主要研究结果

持续部署是企业拥有成熟的DevOps流程后的一项进阶的DevOps实践，它比持续交付更近一步，可以自动化部署更新到生产环境中，而不是其他非生产环境。研发小组不管是部署到生产还是非生产环境，都需要一个工具来实现部署策略。

##### 工具

Jenkins - Jenkins 不仅仅只是一个构建工具，同时也是持续交付解决方案中被采用的最广泛的工具之一。无法计数的Jenkins插件，让其几乎能整合任意工具，包括整个持续交付流程中所有最经典的解决方案。Jenkins插件让开发人员可以通过网络部署docker镜像，部署到Kunenetes机群。使用Pipeline插件，开发人员还可以调用云服务提供商（AWS/Azure）的API通过流程即代码的方式部署任意服务。
 
Azure DevOps - Azure DevOps 是一套微软提供DevOps解决方案，Azure Pipeline是其中的一个服务，它可以用于自动化构建和部署到众多的云提供商，尤其是Azure。

如果贵公司开发了一个.NET、Java、Node、PHP或者Python的App，Azure Pipeline可以帮助您设定一套高度定制化的持续集成和持续交付的流水线。

AWS - AWS CodeBuild 是一套掌控全局的集成服务：编译代码、运行测试、生成带部署的软件包。它还不需要服务器来部署和扩展，也不需要安装、配置和运维任何软件。

AWS CodeBuild是 AWS Code Services家族中的一员，通过AWS Code Services可以创建、完成和自动化软件持续集成和持续交付的发布流程。你也可以只集成Code Build到已存在的CI/CD流程中去。例如: 可以利用Code Build当作已有的Jenkins的一个节点来设置分布式构建。

GitLab - GitLab CI/CD不仅仅只能测试、构建项目，还能够部署到基础设施上。GitLab为每个环境提供完整的部署历史记录，且能够持续追踪部署状态，因此可以查询到当前服务器的部署信息。如果项目连接的是Kubernetes，也可以用它来辅助部署。

GitLab致力于自动化发布与交付应用，缩短交付周期，加速手动流程，提高团队效率。随着无触化持续交付被引入流水线，系统自动获取信息识别做要做的事情，进而实现自动化多环境部署，不管是生产还是非生产环境，甚至实现更加高级的方式，如金丝雀发布。通过特性开关、内置审计/可追溯性、按需环境创建和GitLab的静态内容交付页面，可以实现更有信心的更快速的交付。
 
### 运维

#### 容器

Docker - Docker这一个工具的设计目标是使用容器来更简单的创建、部署和运行应用。Docker容器把软件和其依赖环境结合在一起设置成一个标准化单元来部署，该单元包含运行所需的一切：代码、运行时、系统工具和标准库。企业团体使用Docker容器来保证应用始终运行一致，让协作变得像分享容器镜像一样简单。

Docker不仅仅在这篇DevOps报告中位列容器工具排行榜第一，而且在2019年Stack Overflow的开发者调查显示：Docker还是排名第三的最通用平台，35%专业开发者报告说他们在Docker平台上开发过东西，Docker还是该报告中排名第二的最受喜爱的平台。

Kubernetes - Kubernetes是一个开源的容器编排工具，旨在自动化应用部署，扩展和管理。Kubernetes起初是Google的一个项目，现在由CNCF(云原生计算基金会)维护。
 
Docker 和Kubernetes并不直接竞争，Kubernetes是服务于类似Docker这样的容器平台的容器编排器。主流的云供应商都支持此功能。如果企业打算上云，Kubernetes是个非常可靠的选择。它提供了一个主流的框架来运行分布式系统。每个项目的开发到生产环境，研发小组都能够运行在一致的基础设施之上。Kubernetes可以管理扩展需求，可用性，故障迁移，部署模式等等。

尽管Kubernetes是个健壮的工具，但它的复杂性以及在DevOps工具链中新增的非必需功能也臭名昭著。许多像AWS和Azure的云服务提供商提供的云编排能力就能够满足企业的需要。

AWS - AWS名如其意，是AWS的提供的服务，旨在按需提供云计算平台和对应的API。如果你使用其他的AWS开发者工具来掌管代码、构建、测试和部署服务到AWS，那就应该考虑扩展DevOps工具链，并在AWS上运行容器。

如果贵公司选择了AWS，那么就会涉及一到两个容器编排工具：Amazon的ECS或者EKS。如果对AWS的架构和API熟悉，那么使用ECS来运行容器是更好的选择。因为ECS于AWS的其他服务深度集成，如：IAM、VPC和Amazon Route 53。如果使用Kubernetes，那么EKS是个安全、可靠、可扩展的运行Kubernetes的方式。
 
### 监控

#### 分析/监控

Google Analytics - Google Analytics是一款强大的分析和监控工具，帮助企业团体收集、配置和分析关键数据。该工具提出的洞见可基于用户和网站、网络应用、Android和IOS下的APP交互。开发者可以利用Google Analytics的健壮API来创建综合报告和定制化配置。
 
![](/images/blog/devops-tools-report-2020-051.png )

Grafana - Grafana是一款开源的分析和监测工具，支持十几种用于从源头拉取数据的本地化数据库。它极度可视化，从热力图到直方图，图表到地理图以及各种各样的仪表盘。Grafana还支持团队使用Slack之类的工具发送告警和通知。

![](/images/blog/devops-tools-report-2020-052.png )
 
Azure - Azure 监测器是微软提供的用于对应用、基础设施和网络进行全局可视化监测的工具。通过Azure Monitor遥测技术实现全站监测，触发式告警和获取日志。

![](/images/blog/devops-tools-report-2020-053.png )
 
AWS - AWS CloudWatch向DevOps工程师、研发人员、SRE工程师和IT经理提供监测和分析的服务。CloudWatch提供数据，研发人员采取行动：利用此工具来监测应用，反馈性能变化，优化资源，获取运维健康状况的概览。

CloudWatch以日志形式收集监控和运维数据，度量指标，提供关于运行在AWS或者内部服务器上的资源、应用和服务的相关信息。
 
 ![](/images/blog/devops-tools-report-2020-054.png )


#### 即时通讯

Slack - Slack是一款基于云实例的消息平台，可以拨打视频电话，还基于话题管理频道中的聊天历史记录。它在企业内部被当作实时的邮件使用，研发人员可以获取企业范围内的关键信息和专家的支持，也可以进行项目级的回顾和协作。实时追踪多系统的性能数据以更快速的解决问题，通过衔接其他服务和平台来流线化和自动化工作流程。

Slack集成了主流的项目管理和问题追踪工具，如Jira、GloIssue Boards和Trello，快速响应新增的bug和task，而且无需文档转换。Slack还直接集成进了GitHub、GitLab以及Bitbucket。
 
![](/images/blog/devops-tools-report-2020-055.png )

Microsoft Team - 微软的Teams是一个结合了文字聊天、视频会议、文件存储和应用集成的通讯平台。如果企业依赖于微软工具套装，那么Teams就是理想团队协作的中心。使用Teams可以实时访问、共享、编辑Word、PowerPoint和Excels文件。
 
![](/images/blog/devops-tools-report-2020-056.png )


### 总结

引领性企业还在进行DevOps转型，以通过更安全和快速的交付他们的技术来获取竞争优势。DevOps转型会涉及众多方面，包括员工的思维定式，新技术的教学，合适工具的引进。本报告聚焦于已成功实施这些工具的2700多开拓者，总结出最好的DevOps工具。

把报告分享给其他干系人以展示DevOps转型中工具的重要性。我们的报告明显证明了一点，高效的软件工程师和IT领导会选择有用且可用的工具以在DevOps转型中提升生产力和价值交付；同时也自动和集成新工具到他们的工具链中，释放更多的时间在开发上。这也驳斥了工具实施费时费力的观点。


#### [点此下载原版pdf报告文件](/pdf/devops-tools-report-2020-gitkraken.pdf)

<!-- 
Editor by PikeLiang
Contact:345619151@qq.com
Editing Time:2020-07-23 -->





















































