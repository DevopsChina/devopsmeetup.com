---
title: "如何提高Kubernetes的弹性"
date: 2019-08-27T14:28:54+08:00
description: "Kubernetes 系统的优点是高可用性和弹性，但是在实际使用过程中，由于海量的日志信息给迅速找到 Kubernetes 的故障点造成了困难，从而造成了故障恢复的延误，无法充分发挥 Kubernetes 的优点。本文作者提供了一种容易实现和已经验证了的方法让读者能迅速掌握，从而充分体现和发挥出Kubernetes真正的高可恢复性的能力。"
bgImage: "images/backgrounds/blog-bg.jpg"
bgImageAlt: "ALT-txt"
image: "images/blog/0_Oue3X_Y3apY-n2gM.jpg"
author: "付文新"
postType: "翻译"
summary: "Kubernetes 系统的优点是高可用性和弹性，但是在实际使用过程中，由于海量的日志信息给迅速找到 Kubernetes 的故障点造成了困难，从而造成了故障恢复的延误，无法充分发挥 Kubernetes 的优点。本文作者提供了一种容易实现和已经验证了的方法让读者能迅速掌握，从而充分体现和发挥出Kubernetes真正的高可恢复性的能力。"
type: "post"
categories: 
  - "翻译"
tags:
  - "kubernetes"
  - "HA"
---


>社区译者：付文新

>审校：韦世滴

>原文地址(原作者：Tim Little)：[https://medium.com/kudos-engineering/increasing-resilience-in-Kubernetes-b6ddc9fecf80 ](https://medium.com/kudos-engineering/increasing-resilience-in-Kubernetes-b6ddc9fecf80)



Kubernetes 有两大关键特性：高可用性和弹性。但是当 Kubernetes 集群出现不稳定的时候，我们能做什么呢？眼睁睁看着自己的巨轮沉入深海？


#### Kubernetes 节点问题

我们在使用谷歌 Kubernetes 引擎集群（GKE）时常会遇见这个问题：集群中的 Kubernetes 节点经常性的宕机。

其影响是调度问题节点的容器变得无法响应，我们的监控系统开始大量发送 SLO 和错误预算消费的告警邮件。想更多的了解什么是 SLO 和错误预算告警，以及我们是如何监控的，请查看我之前的一篇[博文](https://medium.com/kudos-engineering/managing-reliability-with-slos-and-error-budgets-37346665abf6)。

通过运行 `gcloud container operations list` 检查命令，我们发现节点会每隔几小时就尝试[自动修复](https://cloud.google.com/kubernetes-engine/docs/how-to/node-auto-repair)。

![](/images/blog/1_uLTkpy6Hv_nuyHNESB6XWg.png)

然而当我们查看 Stackdriver 日志，我们发现了大量的日志，这使得定位问题变得如同海底捞针。

因此我们申请了 Google 的支持，希望可以帮助我们找到问题的根本原因。

不幸的是由于时区差异和我们的账号使用的是遗留支持包的原因，我们每隔24小时才能看到一条 Google 反馈的信息。

最终这个问题耗尽了我们 Kubernetes 中一系列服务的错误预算，因此在真正的 [SRE 风格](https://landing.google.com/sre/sre-book/chapters/embracing-risk/#xref_risk-management_unreliability-budgets)中，我们致力于提高 Kubernetes 集群和 Istio 服务网格的弹性。

#### 增加 kubernetes 服务的弹性

我们首先深入研究了 Kubernetes 集群的设置及运行在它之上的服务，然后确定我们可以增加弹性的范围，主要目的是减少当单个节点无法响应时产生的影响。

- 副本数量和 pod 在不同节点的分布

我们能够改进提升的第一个方面就是增加 Kubernetes [Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/) 的副本数量。我们在 Kudos 上部署了采用微服务架构的服务，这些服务都特别微小，没有状态，特别适合水平扩展。

然而有些 Deployment 只运行一个 pod 上，如果这个 pod 刚巧运行在发生问题的节点上，我们的服务就会中断。因此我们修改了 Deployment，运行至少3个副本以提高弹性。

当时我们只有3个节点（现在14个），这导致了另外一个问题：有时 Kubernetes 会调度所有 pod 到同一个节点上。

因此我们使用了 Kubernetes 的一个名为 [Pod AntiAffinity](https://kubernetes.io/docs/concepts/configuration/assign-pod-node/#affinity-and-anti-affinity) 的功能特性：如果某个节点已经包含具有相同标签（例如：`app=<service-name>`）的 pod，该特性将指示调度程序把该节点标记为不可调度。

``` yaml
affinity:
    podAntiAffinity:
      preferredDuringSchedulingIgnoredDuringExecution:
      - weight: 100
        podAffinityTerm:
          labelSelector:
            matchExpressions:
            - key: app
              operator: In
              values:
              - <service-name>
          topologyKey: "kubernetes.io/hostname"
```

添加了这些内容并重新部署了所有服务之后，我通过运行 `kubectl	get	pods	-o customcolumns=’NAME:.metadata.name,NODENAME:.spec.nodeName` 命令验证了 pod 被调度到不同的节点上。

现在如果我们的一个节点再次宕机，我们也只损失了部署的3个 pod 中的一个，我们的服务仍然可用。

- 就绪探针与预停命令

我们注意到另一个问题是当节点被修复时，Kubernetes 会在节点准备就绪之前就开始发送流量。在升级 Kubernetes 节点池的时候也遇到过类似问题，但我们从未深究其因。

经过 Google 一番之后，我们发现一篇关于[零停机滚动更新](https://blog.sebastian-daschner.com/entries/zero-downtime-updates-kubernetes)的博客。这篇博客的主要内容之一是关于把 pod 标记为终止，并从负载均衡中将其删除的异步特性。

>这种重新配置是异步进行的，因此不能保证其按照正确的顺序，从而导致不少请求被分发到终止的 pod 上，进而致使请求崩溃。

从此以后，我们在所有的服务上都增加了[Readiness probes](https://kubernetes.io/docs/tasks/configure-pod-container/configure-liveness-readiness-probes/#define-readiness-probes)(就绪探针)，并增加[preStop](https://kubernetes.io/docs/tasks/configure-pod-container/attach-handler-lifecycle-event/#define-poststart-and-prestop-handlers)(预停)命令：该命令会等待10秒后终止，以允许这些少数连接仍然可用。

```yaml
readinessProbe:
  httpGet:
    path: /readiness
    port: 8080
  initialDelaySeconds: 15
lifecycle:
  preStop:
    exec:
      command: ["/bin/sh","-c","sleep 10"]
```

- Istio 水平自动伸缩

随着 Kubernetes 的进一步稳定，我们注意到集群中另一个单点故障：Istio。

我们把 Istio 当做谷歌 Kubernetes 引擎（GKE）的[附加组件](https://cloud.google.com/istio/docs/istio-on-gke/overview)使用，这使得我们可以使用 Istio，并且不需要额外的操作开销来管理 Istio 的控制面板。

Istio 使我们能够按路线分发流量到网络中的任意服务中去，而不需要每个服务都有一个公共的 IP 地址。

它通过入口网关（Ingressgateway）来实现这一点，该网关是一个位于网络边缘的代理（Envoy）网关，并且连接到 Google 的负载均衡器上，以便获取访问外部网络的权限。

我们遇到的问题是谷歌 Kubernetes 引擎（GKE）附加组件默认的 Istio 只在一个 pod 中部署入口网关（Ingressgateway）。这就意味着一旦该节点忽然宕机，我们就无法访问网络中的所有服务。

这肯定不是理想方案，因此我们研究了下 Istio 的设置，结果发现 Google 早就意识到这一点，可以通过[部署 HorizontalPodAutoscaler](https://cloud.google.com/istio/docs/istio-on-gke/overview#modifying_control_plane_settings) 来修改 Istio 的控制面板。为此，我们需要用这个命令 `kubectl edit -n istio-system Deployments/istio-telemetry` 向 Istio 控制面板组件添加资源请求，之后在容器中添加以下内容：

```yaml
resources:
   requests:
     cpu: 100m
```

这使得 [HorizontalPodAutoscaler](https://kubernetes.io/docs/tasks/run-application/horizontal-pod-autoscale/) 可以检测 Pod 的 CPU 利用率，并相应的进行伸缩或扩展。就如同我们之前为其他服务所做的一样，我们还编辑了 HorizontalPodAutoscaler，使其至少有3个副本在运行。

![](/images/blog/1_2Trt6VFzq_sy8oCCugVj5Q.png)


#### 根源分析

在解决弹性问题的期间，我们一直和 Google 的支持团队保持联系。

支持团队建议我们深入查看下 Kubernetes 的节点，并怀疑这是一个资源耗尽的问题。

在对节点进行了一些故障排除之后，我们发现一些节点上的进程 ID 中出现了泄露，`<defunct>` 进程树中数以千计的进程没有被正确终止。

![](/images/blog/1_QhWh1fkOTFRVHj4yKxEAsw.png)

检查了父进程 ID 之后，我们发现了问题所在。

![](/images/blog/1_eR1MBSDzzgu4HGdNbDX6jQ.png)


该`3491355` 进程是我们其中的一个容器，它用来转换 HTML 页面到 PDF，使用的是 Google 的 Chrome 实例来实现这一点。

这个无头服务有一个名为 `/readiness` 用来检查 Google Chrome 版本的程序，但是该程序只抓取了版本信息文件，`cat`进程并没有被正确的结束。

我们之后修改了程序 readiness，并重新部署了 pdfgenerator 服务，然后我们看到运行该服务的节点中 PID 数量大幅减少。

Kubernetes 开发团队预见了这个问题，并在1.14 版本中引入了 PID 限制。可惜的是我们生产环境运行的1.13版本，没能够赶上这个变化。

#### 结论

在这些问题背后，我们学到了大量关于 Kubernetes 和 Istio 的知识。我们更新了自己的微服务模板，使部署到我们集群中的默认微服务更有弹性，而且扩展了集群以帮助支持新服务。

如果你对这些都感兴趣，为什么不考虑[加入Kudos](https://www.growkudos.com/about/careers)？
