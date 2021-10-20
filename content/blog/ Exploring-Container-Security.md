---
title: "探索容器安全性：运行你所信任的，其它的则隔离"
date: 2020-03-02T21:05:12+08:00
description: "从漏洞到加密劫持，再到更多的加密劫持，在整个2019年都有大量安全事件使容器用户保持警惕。随着Kubernetes被用于管理大多数基于容器的环境（以及越来越多的混合环境），对于Forrester研究人员来说不足为奇，在他们2020年的预测中指出，需要“在日益混杂的云世界中保护应用程序和数据的安全"
bgImage: "images/blog/exploring-container-security.png"
bgImageAlt: "ALT-txt"
image: "images/blog/exploring-container-security.png"
author: "吴林伟"
postType: "翻译"
summary: "从漏洞到加密劫持，再到更多的加密劫持，在整个2019年都有大量安全事件使容器用户保持警惕。随着Kubernetes被用于管理大多数基于容器的环境（以及越来越多的混合环境），对于Forrester研究人员来说不足为奇，在他们2020年的预测中指出，需要“在日益混杂的云世界中保护应用程序和数据的安全"
type: "post"
categories: 
  - "翻译"
tags:
  - "kubernetes"
  - "docker"
  - "containers"
---

>社区译者：吴林伟  
审校：张彪  
原作者：Aparna Sinha，Sampath Srinivas  
原文地址：[https://cloud.google.com/blog/products/containers-kubernetes/kubernetes-engine-features-and-guidance-to-help-lock-down-your-containers/](https://cloud.google.com/blog/products/containers-kubernetes/kubernetes-engine-features-and-guidance-to-help-lock-down-your-containers/)

从 **漏洞** 到 **加密劫持，再到更多的加密劫持**，在整个2019年都有大量安全事件使容器用户保持警惕。随着Kubernetes被用于管理大多数基于容器的环境（以及越来越多的**混合**环境），对于Forrester研究人员来说不足为奇，在他们2020年的预测中指出，需要**“在日益混杂的云世界中保护应用程序和数据的安全”**。

无论您是使用Google Kubernetes Engine还是与Anthos混合使用，我们Google Cloud容器安全团队都想让您的容器被很好的保护，并让您全面了解容器的安全性。在2020年开始之际，这里有一些有关如何保护Kubernetes环境的建议，以及有关GKE最新的功能和资源。

### 仅运行你所信任的, 从硬件到服务 
我们在2019年看到的许多漏洞都通过另一个过于受信任的组件破坏了容器供应链或特权提升。重要的是，您必须信任自己运行的服务，并在容器中应用纵深防御原则。为了帮助您做到这一点，现在可以普遍使用[Shielded GKE](https://cloud.google.com/blog/products/identity-security/exploring-container-security-bringing-shielded-vms-to-gke-with-shielded-gke-nodes)节点，并且不久之后即可使用[Workload Identity](https://cloud.google.com/blog/products/containers-kubernetes/introducing-workload-identity-better-authentication-for-your-gke-applications)，这是一种将GKE应用程序验证到其他Google Cloud服务的身份的方法，该方法遵循最佳实践的安全原则（比如纵深防御原则）。

让我们更深入地研究这些功能。

#### Shielded GKE节点
Shielded GKE节点可确保集群中运行的节点是Google数据中心中经过验证的节点。通过将Shielded VM的概念扩展到GKE节点，Shielded GKE节点从两个方面提高了基准GKE安全性：

***节点操作系统的来源检查：***  
    可通过密码验证的检查，以确保节点操作系统在Google数据中心的虚拟机上运行。  
***增强的rootkit和bootkit保护：***  
    安全和可衡量的启动，虚拟可信平台模块（vTPM），UEFI固件和完整性监控。   

现在，你在创建新群集或升级现有群集时，可以打开这些“Shielded GKE节点”保护。有关更多信息，请阅读[文档](https://cloud.google.com/kubernetes-engine/docs/how-to/shielded-gke-nodes)。

#### Workload Identity

您的GKE应用程序可能使用其他服务（例如数据仓库）来完成其工作。例如，以“仅运行您所信任的内容”为宗旨，当应用程序与数据仓库进行交互时，该仓库将要求对您的应用程序进行身份验证。从历史上看，这样做的方法与安全性原则不符，它们过于宽松的被授权，如果受到威胁，则有可能产生较大的影响。

Workload Identity可帮助您遵循最小特权原则，并通过具有短期凭证的Google托管服务帐户自动进行工作负载身份验证，从而降低影响。在[beta版博客](https://cloud.google.com/blog/products/containers-kubernetes/introducing-workload-identity-better-authentication-for-your-gke-applications)和[文档中](https://cloud.google.com/kubernetes-engine/docs/how-to/workload-identity)了解有关Workload Identity的更多信息。我们将很快推出Workload Identity的一般可用性。


#### 增强您对不信任的工作负载的安全性

但是有时候，您不能放心地信任正在运行的服务。例如，一个应用程序可能使用了组织外部产生的代码，或者可能是一个软件即服务（SaaS）应用程序，它接收了来自未知用户的输入。对于这些不受信任的工作负载，工作负载与主机资源之间的第二层隔离是遵循深度防御安全性原则的一部分。为了帮助您做到这一点，我们发布了[GKE沙盒](https://cloud.google.com/kubernetes-engine/sandbox)的一般可用性。

#### GKE沙盒

GKE沙盒使用开源容器运行时[gVisor](https://gvisor.dev/)额外隔离一层来运行容器，而无需更改应用程序或与容器进行交互的方式。gVisor使用用户空间内核来拦截和处理系统调用，从而减少了容器与主机之间的直接交互，进而减少了攻击面。但是作为一项托管服，GKE沙盒提取了这些内部信息，使您可以只需一步即可简化多层保护。[让我们开始熟悉和使用GKE沙盒](https://cloud.google.com/kubernetes-engine/sandbox/)。


## 提升您的容器安全知识

随着越来越多的公司使用容器和Kubernetes对其应用程序进行现代化改造，决策者和业务领导者需要了解它们如何应用于他们的业务以及如何帮助保证业务安全。

#### 容器安全的核心概念

《[为什么容器安全对您的业务至关重要](https://services.google.com/fh/files/misc/why_container_security_matters.pdf)》是专门为不熟悉容器和Kubernetes的读者而写的，它将带您了解容器安全的核心概念，例如供应链和runtime安全。无论您是自己运行Kubernetes还是通过GKE或Anthos等托管服务，此白皮书都将帮助您了解譬如Kubernetes等开源软件如何响应漏洞以及这对您的组织有什么重要的意义。

#### 新的GKE多租户最佳实践指南

当租户之间共享一个或多个集群时，多租户通常被实现为节省成本或提高生产力的机制。但是，将集群错误地配置为具有多个租户或相应的计算或存储资源，不仅不会节省的成本，而且还会使暴露的租户容易受到各种攻击。我们刚刚发布了[新指南GKE企业多租户最佳实践](https://github.com/GoogleCloudPlatform/gke-enterprise-mt)，它可以指导您设置多租户集群，并着眼于可靠性，安全性和监控。阅读新指南查看相应的Terraform模块，并提高多租户安全性。

#### 了解Google如何在内部处理云原生安全性

正如业界正在从基于单一应用程序的架构过渡到分布式云原生微服务一样，Google也一直在从基于边界的安全性过渡到云原生安全性。

在两个新的白皮书中，我们发布了有关内部如何执行此操作的详细信息，包括云原生安全性背后的安全性原则。了解有关[BeyondProd](https://cloud.google.com/blog/products/identity-security/beyondprod-whitepaper-discusses-cloud-native-security-at-google)（Google的原生云安全模型）的更多信息；关于[Borg的二进制授权](https://cloud.google.com/security/binary-authorization-for-borg/)，它讨论了我们如何确保代码出处保护和代码身份认证。


## 让2020年成为您的容器安全年

安全是一个持续的过程。无论您是刚开始使用GKE还是已经使用Anthos在云中运行集群，请随时了解[Google的最新容器安全功能](https://cloud.google.com/containers/security/)，并在[集群增强指南](https://cloud.google.com/kubernetes-engine/docs/how-to/hardening-your-cluster)中了解如何实施它们。
