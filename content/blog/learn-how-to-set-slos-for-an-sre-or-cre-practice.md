---
title: "学习和传授服务水平/质量目标的技艺 ---- CRE课程"
date: 2020-03-09T08:15:40+08:00
description: "客户可靠性工程(CRE)团队帮助 Google Cloud 的许多客户创建了他们的第一个 SLO，并更好地帮助他们了解其服务的可靠性。我们希望各地的团队都能执行这些原则。我们很高兴地宣布，在 CC-BY 4.0 许可下，我们的 SLO 技艺工作室将免费提供所有材料，只要认定 Google 是原始作者，任何人都可以使用或重复使用。在过去的一年中，我们一直邀请世界各地的客户来参加我们的研讨会。从现在开始，任何人都可以实行他们自己的版本，来指导他们的同事、客户或会议与会者为什么所有的服务都需要 SLO。"
bgImage: "images/backgrounds/blog-bg.jpg"
bgImageAlt: "ALT-txt"
image: "images/blog/learn-how-to-set-slos-for-an-sre-or-cre-practice.png"
author: "张洁"
postType: "翻译"
type: "post"
summary: "在理解 Art of SLO 的时候，我一直在考虑这里的art是理解为艺术么？带着这个问题，结合我自己的工作经验，开始在 cloud.google 网站中寻找答案。一般意义上，艺术往往带有很强的个人感悟能力，而对于做技术的IT人员来说，有故作玄虚之态，因此我理解这里的 Art 更多的是传递一种匠人的技艺精神，也就是可以通过不断的学习、思考、总结，达到更高的水平。这一篇文章应该算是抛砖引玉，希望能激发更多的IT人员，通过不断的学习、思考、总结，达到自己理想的水平和能力。"
categories: 
  - "翻译"
tags:
  - "SLO"
  - "CRE"
---

>社区译者：张洁  
审校：吕益行  
原作者：Alex Bramley  
原文地址：[https://cloud.google.com/blog/products/management-tools/learn-how-to-set-slos-for-an-sre-or-cre-practice](https://cloud.google.com/blog/products/management-tools/learn-how-to-set-slos-for-an-sre-or-cre-practice)

一直热衷 [CRE Life Lessons](https://cloud.google.com/blog/topics/cre-life-lessons) 博客系列文章的读者们（我们有几十个这样的人!）能够理解[调优的服务级别指示器(SLI)和服务水平目标(SLO)](https://cloud.google.com/blog/products/gcp/available-or-not-that-is-the-question)的价值。这些概念是站点可靠性工程(SRE)实践的基本构件。毕竟，在没有可以适当度量可靠性指标的情况下，对于您希望实现的服务可靠性，如何讨论更有意义呢?

客户可靠性工程(CRE)团队帮助 Google Cloud 的许多客户创建了他们的第一个 SLO，并更好地帮助他们了解其服务的可靠性。我们希望各地的团队都能执行这些原则。我们很高兴地宣布，在 [CC-BY 4.0](https://creativecommons.org/licenses/by/4.0)许可下，我们的 SLO 技艺工作室将免费提供所有材料，只要认定 Google 是原始作者，任何人都可以使用或重复使用。在过去的一年中，我们一直邀请世界各地的客户来参加我们的研讨会。从现在开始，任何人都可以实行他们自己的版本，来指导他们的同事、客户或会议与会者为什么所有的服务都需要 SLO。

#### SLO 的技艺涵盖了什么

SLO 技艺工作室，向来自开发、运营、产品和业务领域的观众，传授了开发 SLO 的基本元素。研讨会的幻灯片附有一份28页的参与者支持手册，它是参与者解决实际问题的部分参考资料和背景资料。

在研讨会中，我们基于两个基本的认知，以一个业务案例的方式提出 SLO 的价值。基本认知之一，可靠性是任何服务最重要的特性。基本认知其二，100%的可靠性目标对任何事情来说都是不现实的。这些认知是错误预算(error budget)的概念的基础，即在给定的时间范围内，由接近100%的 SLO 目标所引起的允许错误的非零数量。快速的创新和服务的可靠性之间的紧张关系，在不耗尽错误预算的情况下，尽可能快地推出新特性来解决。

一旦每个人(希望如此)都相信 SLO 是一件好事，我们将解释，通过生产环境中运行服务产生的大量遥测数据，如何选择好的 SLI，并介绍 SLI 方程，这是我们推荐的通用 SLI 的方法。我们介绍了，设置第一个 SLO 目标的两种替代方法，两种方法取决于不同的考量，并提供了如何随着时间的推移聚合这些目标的建议。我们将介绍一个实际的示例—服务器端基础设施，它支持一个名为 Fang Faction 的虚拟手机游戏—并使用它来演示如何将SLI从一个简单的、通用的规范，细化为一个可以由监控系统测量的具体实现。

至关重要的是，参与者将这些新获得的知识直接应用到实践中，为 Fang Faction 开发了更多的 SLI 和 SLO。通常，当我们与客户一起组织这个研讨会时，我们会将他们大致分成8个小组，并让他们在90分钟内解决研讨会上的问题。每个小组都配有一名经验丰富的 SRE 志愿者，他会促进讨论，鼓励参与，并保障小组不偏离讨论。

#### 组织自己的 SLO 工作室!

如果你对这一切感兴趣，你可以从支持手册中获取信息，手册中包含了关于如何组织 SLO 工作室的更多信息。如果你没有一个完整的团队需要培训，你可能会对我们在 Coursera 上[《可靠性测量和管理》](https://cloud.google.com/blog/products/devops-sre/introducing-a-new-coursera-course-on-site-reliability-engineering)的课程感兴趣，这是一门更全面、可以自行设定学习进度的课程，深入了解、学习 SLI、SLO 和 error budget 的世界。
