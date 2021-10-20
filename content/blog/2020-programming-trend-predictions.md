---
title: "2020年及未来的软件编程趋势预测"
date: 2019-09-18T15:21:59+08:00
description: "如果您对未来可能给编程世界带来什么感到好奇，那么读这篇文章就对了。我也有可能错了，所以请不要盲目的相信我，但这就是我认为会发生的事情。我无法预测未来，但我可以做出有根据的猜测。"
bgImage: "images/backgrounds/blog-bg.jpg"
bgImageAlt: "ALT-txt"
image: "images/blog/1_eHc3cNEAM9kro06WSPQG3w.jpeg"
author: "李杰"
postType: "翻译"
summary: "如果您对未来可能给编程世界带来什么感到好奇，那么读这篇文章就对了。我也有可能错了，所以请不要盲目的相信我，但这就是我认为会发生的事情。我无法预测未来，但我可以做出有根据的猜测。"
type: "post"
categories: 
  - "翻译"
tags:
  - "Rust"
  - "React"
---

>社区译者：李杰

>审校：韦世滴

>原文地址(原作者：Indrek Lasn)：[https://medium.com/better-programming/2020-programming-trend-predictions-a5d6b70bec26](https://medium.com/better-programming/2020-programming-trend-predictions-a5d6b70bec26)


2020年马上就要到了，这听起来很疯狂。似乎2020年就像是科幻小说里的故事那么遥远，但我们在这里 --- 即将敲开它的大门。

如果您对未来可能给编程世界带来什么感到好奇，那么读这篇文章就对了。我也有可能错了 –-- 所以请不要盲目的相信我 --- 但这就是我认为会发生的事情。我无法预测未来，但我可以做出有根据的猜测。

**“预测未来的最好方法就是创造它。” ----- 亚伯拉罕·林肯**

#### Rust 将会成为主流

![](/images/blog/1_URxLxrhx6uW2I9iy-KWNZw.png)

[Rust](https://en.wikipedia.org/wiki/Rust_(programming_language)) 是一种多范式的系统编程语言，专注于安全性 --- 尤其是并发的安全性。Rust 在语法上与 C++ 类似，但它旨在提供更好的内存安全性的同时保持高性能。

![](/images/blog/1_MlmBiU91g7RWBirNd6IBJQ.png)

我们已经看到了 Rust 编程语言四年的强劲增长。我认为2020年将是 Rust 正式成为主流的一年。虽然主流的定义通常是源于自我的解释，但我相信学校将开始将 Rust 引入他们的课程。这将创造一批新的 Rust 工程师。

![](/images/blog/1_URWiaCRe_gXFmjzIGCNx9Q.png)

Rust 已经证明自己是一门优秀的语言，并且它拥有一个充满活力和活跃的社区。随着 Facebook 在 Rust 上建立 [Libra](https://levelup.gitconnected.com/getting-started-with-the-facebook-libra-programming-language-a1d21aa837e0) --- 这个 Facebook 有史以来最大的项目 --- 我们即将看到 Rust 真正取得的成就。

如果你想学习一门新语言，我强烈建议学习 Rust。推荐阅读《Go Rust！》这本书开始你的 Rust 学习之旅，你会从中学到很多知识。 

#### GraphQL 将继续增长

![](/images/blog/1_rijcw7aVJwAqCJG5KT-nJg.png)

现在我们的应用程序以及对数据使用的方式变得越来越复杂。这就需要一种比传统 REST API 更加优秀的解决方案，多次使用 GraphQL 的经历使我成为了 GraphQL 的忠实粉丝。

典型的 REST API 需要从多个 URL 加载，但 GraphQL API 可以在单个请求中获取您的应用程序所需的所有数据。

![](/images/blog/graphql.png)

GraphQL 已经在各种规模的团队和许多不同的环境、语言中使用，它支持移动应用程序，网站和 API。

![](/images/blog/or-graphql.png)

如果您对学习 GraphQL 感兴趣，请查看[我写的教程](https://medium.com/better-programming/how-to-setup-a-powerful-api-with-graphql-koa-and-mongodb-339cfae832a1)。

#### 渐进式 Web 应用程序

渐进式 Web 应用程序（PWA）是一种通过将 Web 的最佳功能与移动应用程序的顶级特性相结合来构建应用程序的新方法。

![](/images/blog/web-native.png)

相比于原生平台的开发人员，Web 开发人员的数量要多的多。我相信一旦大公司意识到他们可以重新利用他们的 Web 开发人员来制作渐进式网页应用程序，将来将会产生大量的 PWA 开发人员。

当然，大型公司需要一段时间才能适应，这对于技术来说是再正常不过的。

这部分开发工作通常会划入前端开发的范畴，因为它的主要交互方式是与 Web Workers API（Native Browser API）进行交互。

纯原生的 Web 应用程序将越来越艰难。越来越多的人开始认识到，编写一个跨平台的 PWA 程序可以在减少工作量的同时产生更多价值。

![](/images/blog/google-data.png)

今天是开始了解更多 PWA 的完美日子，从这里[开始](https://medium.com/better-programming/everything-you-need-to-know-about-pwas-8e41a7e745aa)。

#### 网页内嵌程序将迎来曙光

WebAssembly（缩写为 Wasm）是一种基于概念机的机器语言。它非常轻便，可以用于编译 C，C++ 和 Rust 等高级语言。Wasm 还支持在 Web 上部署客户端和服务器应用程序。PWA 也可以使用 Wasm 来编写。

换句话说，WebAssembly 是一种将 JavaScript 技术与更多级别技术相结合的方法。请想象一下在 React 应用程序中使用 Rust 图像处理库 –-- Wasm 将上述设想变为现实。

众所周知性能的重要性，随着数据量的增长，保持良好性能将更加困难。这也正是 C++ 或 Rust 等底层语言发挥作用的时候。我们将看到越来越多的大公司开始采用 Web Assembly。

#### React 将继续统治

![](/images/blog/javascript-img.png)

React 是迄今为止最受欢迎的前端开发 JavaScript 库。构建 React 应用程序很有趣也很容易。就构建应用程序的经验而言，React 团队和社区已经做了出色的工作。

![](/images/blog/react-img.png)

我曾经使用过 Vue，Angular 和 React，我认为它们都是很棒的框架。但是，框架的目标是完成工作，所以完成工作是最重要的事情。争论什么框架是“最好的”是完全没有意义的。选择一个框架并将你所有的精力用于完成工作才是正途。

如果您有灵感，请从此[列表](https://medium.com/better-programming/the-secret-to-being-a-top-developer-is-building-things-heres-a-list-of-fun-apps-to-build-aac61ac0736c)中选择一些内容并立即开始构建！

#### 赌 JavaScript 就对了

我可以充满信心地说，2010年是 JavaScript 的十年。我们已经看到了 JavaScript 的巨大增长，并且它似乎没有放缓。

JavaScript 开发人员曾被称为“不是真正的开发人员”。可事实上 JavaScript 是任何大型科技公司的核心，例如 Netflix，Facebook，Google 等等。因此，JavaScript 作为一种语言与任何其他编程语言一样合法。人们应以成为 JavaScript 开发人员为荣。毕竟，JavaScript 社区已经构建了一些很酷且具创新性的东西。

几乎所有网站都在某种程度上使用了 JavaScript。有多少个网站呢？上百万个！

现在是成为 JavaScript 开发人员的最佳时机。工资正在上涨，社区一如既往地活跃，就业市场巨大。如果你对学习 JavaScript 很感兴趣，那么我推荐[“你不懂 JS”](https://amzn.to/2YzFmcq)系列丛书。

![](/images/blog/paihang-lan.png)

我之前写过[关于 JavaScript 流行](https://medium.com/better-programming/what-makes-javascript-javascript-b9ab51ad983a)的文章 - 你也应该读一读。

![](/images/blog/open-img.png)

我是否落下了很酷的项目？让我们知道哪些项目或语言值得更多的关注和爱戴！








