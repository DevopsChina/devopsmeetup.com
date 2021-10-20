---
title: "DevOps和SRE工程师必需知道的检查清单"
date: 2019-10-17T11:14:50+08:00
description: "本文清晰列举成为一名合格的DevOps和SRE工程师所需的知识图谱，阅读本文对新入门的学习者将大有裨益。"
bgImage: "images/backgrounds/blog-bg.jpg"
bgImageAlt: "ALT-txt"
image: "images/blog/devops-and-sre-lists.jpg"
author: "陈文峰"
postType: "翻译"
summary: "本文清晰列举成为一名合格的DevOps和SRE工程师所需的知识图谱，阅读本文对新入门的学习者将大有裨益。"
type: "post"
categories: 
  - "翻译"
tags:
  - "DevOps"
  - "SRE"
---

>社区译者：陈文峰  
审校：韦世滴  
原作者:Aymen El Amri and Sahil Sharma  
(原文地址)：[https://medium.com/faun/the-must-know-checklist-for-devops-site-reliability-engineers-update-8ba44dbc824](https://medium.com/faun/the-must-know-checklist-for-devops-site-reliability-engineers-update-8ba44dbc824)

对于布道者来说，DevOps 是一种文化和转型。对于一些工程师来说，DevOps 是一套敏捷的工具和技术的集合。对于经理来说，DevOps 可能是一种方法论。对于其他人来说，这只是一个时髦术语；对于招聘者来说，DevOps 是一份职位。

我认为 DevOps 不仅仅是一个流行语，但不知何故它变成了以上所有定义的混合：如果没有正确的方法论、合适的工具集和合适的工程师，就没办法完成数字化的转型。

在上一篇文章中，我写了15点 DevOps 检查列表，描述了在业务中实施 DevOps 的方法。这篇文章更多关于 DevOps、SRE 工程师所需的技能。下面列出的许多要点都是针对 *nix 环境的，这并不意味着适合 Windows 爱好者的 DevOps 环境。

这个清单并非详尽完整的，仅列举了基础的技术，必须知道的技能和一些即兴的想法。您可以将它们用作评估清单来评估您自己或其他人，或为您的下一次 DevOps/SRE 工作面试做准备。

这个清单是个人人坚持推荐的清单。

1. 首先，一定要了解文化要点的重要性，可以通过点击这里了解更多 [DevOps 15项检查表](https://medium.com/devopslinks/the-15-point-devops-check-list-8cd2afb4a448)。
2. 您需要掌握 *nix 系统，并充分了解 Linux 任务调度的工作原理。
3. 不用担心终端，您可能有 GUI 界面来管理您的服务器。但无论是什么情况，您都必须爱上终端，它更快、更安全、更诚实，一旦掌握它就非常容易使用。
4. 如何获取 CPU 和系统信息（如 `cat /proc/version`、`cat /proc/cpuinfo`、`uptime` ...）。
5. Cron 任务如何运作。如何将 cron 任务设置在指定日期/时间/月。
6. 如何知道您在计算机上运行的操作系统是什么版本（`cat /etc/lsb-release`）
7. 了解不同的 *nix 操作系统之间的差异以及如何知道您在计算机上运行的操作系统是什么版本（例如`cat /etc/lsb-release`）。
8. 几个 shell 命令之间的区别：`sh`，`dash`，`bash`，`ash`，`zsh` 。
9. 如何设置和取消设置 ENV 变量。导出 ENV 变量是暂时的，如何导出永久变量？
10. 什么是 shell 配置文件：例如 `~/.bashrc`，`.bash_profile`，`.environment` ，如何操作程序初始化文件的配置源码。
11. 必需了解 Vim、它的配置（`.vimrc`）及其一些基本技巧。
12. 日志如何在 *nix 系统中运行，什么是日志记录级别以及如何使用日志管理工具（`rsyslog`，`logstash`，`fluentd`，`logwatch`，`awslogs`  ...）。
13. 交换分区如何工作的。什么是交换性。（`swapon -s，/proc/sys/vm/swappiness，sysctl vm.swappiness`  ...）。
14. 如何在查看/设置网络配置。
15. 如何在具有不同子网的计算机上设置静态/动态 IP 地址？ （提示：`CIDR`）
16. 如何查看/设置/备份您的路由器设置？
17. DNS 如何工作？如何设置 DNS 服务器（`Bind，Unbound，PowerDNS，Dnsmasq` ...）？递归和权威 DNS 有什么区别？如何解决 DNS 故障（`nslookup，dig` ...）。
18. 熟悉 DNS 和 A，AAAA，C，CNAME，TXT 记录。
19. SSH 如何工作，如何调试它以及如何生成 ssh 密钥以及无密码登录到其他计算机。
20. 如何设置 Web 服务器（`Apache，Nginx` ...）。
21. Nginx 和 Apache 有什么区别？什么时候使用 Nginx？什么时候使用 Apache？您可以在同一个 Web 应用程序中使用它们，何时以及如何使用它们？
22. 如何设置反向代理（`Nginx` ...）。
23. 如何设置缓存服务器（`Squid，Nginx` ...）。
24. 如何设置负载均衡（`HAproxy，Nginx` ...）。
25. 什么是 init 进程？你知道 `Systemd`（自 Ubuntu 15.04 开始使用），`Upstart`（由 Ubuntu 开发），`SysV` ...
26. 熟悉 Systemd 以及如何使用 `systemctl` 和 `journalctl` 等命令分析和管理服务。
27. 从源代码编译任何软件（`gcc`、`make` 和其他相关内容）。
28. 如何通过终端压缩/解压缩不同格式的文件（主要是：`tar`/`tar.gz`）。
29. 如何设置防火墙（使用 `iptables` 或至少为 `ufw`）：设置规则、列表规则、路由流量、阻塞协议/端口 ...。
30. 了解最常用的默认运行服务端口号（如：SSH（22），Web（80），HTTPS（443）等）。
31. 了解如何在生产环境中实时调试和跟踪运行的应用程序。
32. 能轻松自如使用脚本语言。Bash 是必须掌握的（其他脚本语言也非常有用，如 `Python，Perl` ...）。
33. 了解如何使用至少一个配置管理和远程执行工具（`Ansible`，`Puppet`，`SaltStack`，`Chef` 等）。您的选择应基于以下标准：语法、性能、模板语言、推送与拉取模型、架构、与其他工具的集成、可扩展性、可靠性等。
34. 了解如何配置和使用持续集成和持续交付工具，如 Jenkins、Travis CI、Buildbot、GoCd。将这些工具与其他工具（如 Selenium、构建工具、配置管理软件、Docker、云提供商的 SDK 等）集成是非常价值的。
45. 学习分布式版本控制系统 Git 及其基本命令（`pull` / `push` / `commit` / `clone` / `branch` / `merge` / `logs` 等）。了解 Git 工作流程。你知道如何将 Git 存储库恢复到上一个的提交吗？
36. 了解如何使用 SSH 密钥。尝试使用 Github、Bitbucket 或 Gitlab 等来配置对 repo / account 的无密码访问。
37. 熟悉 Vagrant 等工具，使用它们创建可分发和可移植的开发环境。
38. 开始研究基础设施即为代码和基础设施配置自动化工具（如 Terraform 和 Packer）。
39. 开始研究容器和 Docker。它的底层机制（cgroups 和命名空间）怎么运行？
40. 开始熟悉基本的 Docker 命令（`logs` / `inspect` / `top` / `ps` / `rm`），另请查阅 docker hub（推/拉镜像）。
41. 开始研究容器编排工具：Docker Swarm，Kubernetes，Mesosphere DC / OS，AWS ECS。
42. 深入研究 DB（MySQL 或任何其他你喜欢的）。
43. 学习 Redis / Memcache 和类似工具。
44. 你的备份策略是什么？如何测试备份是否可靠。
45. 你知道 ext4、ntfs、fat 吗？你知道 Union 文件系统吗？
46. 发展您的云计算技能。首先选择云基础架构提供商：Amazon Web Services、Google Cloud Platform、Digitalocean、Microsoft Azure。或者使用 OpenStack 创建自己的私有云。
47. 那么模拟服务器呢？您的单元测试测试策略是什么？端到端？那你真的需要模拟服务器吗？谷歌“模拟服务器必将消失”。
48. 阅读有关 PaaS / Iaas / Saas / CaaS / FaaS / DaaS 和无服务器架构的知识。
49. 了解如何使用 Cloud Shell 从您的 CLI 或使用 Cloud SDK 的程序中使用和配置云资源。
50. 您熟悉 OSI 模型和 TCP / IP 协议规范吗？ TCP 和 UDP 有什么差别？你知道 vxlan 吗？
51. 掌握实用的命令，如进程监控命令（`ps，top，htop，atop` ...），系统性能命令（`nmon，iostat，sar，vmstat` ...）和网络故障排除和分析（`nmap，tcpdump，ping，traceroute，airmon，airodump` ...）。
52. 了解 HTTP 状态代码（`2xx，3xx，4xx，5xx`）。
53. 你熟悉 IDE（Sublime Text，Atom，Eclipse 等）吗？
54. 网络数据包分析：`tcpdump、Wireshark `等工具。
55. 当你在浏览器中点击 google.com 时会发生什么？从浏览器的缓存，本地 DNS 缓存，本地网络配置（主机文件），路由，DNS，网络，Web 协议，缓存系统到 Web 服务器（如果深入讨论的话最基本的问题都是很难的）。
56. 熟悉混乱的内核版本以及如何更新补丁。
57. 熟悉 SSL / TLS 的工作原理以及数字证书的工作原理（https）。
58. 熟悉安全协议：TLS，STARTTLS，SSL，HTTPS，SCP，SSH，SFTP，FTPS 等。
59. 了解 PPTP，OpenVPN，L2TP / IPSec 之间的差异。
60. 如何生成校验串（`md5`，`SHA` ...）来验证任何文件的完整性。
61. 了解整体架构和微服务架构之间的区别。
62. 了解微服务架构的优缺点，并开始构建类似的架构。
63. 你知道什么是 ChatOps 吗？您是否尝试过使用其中一个已知框架？ Hubot，Lita，Cog？
64. 如何实现零停机部署？您制定回滚、自我修复、自动扩展的策略是什么？
65. 熟悉 API 和服务：RESTfull，类 RESTful，API 网关，Lambda 函数，无服务器计算，SOA，SOAP，JMS，CRUD。
66. 学习有关无状态和有状态的应用程序。
67. 阅读 DevOps 相关词汇表（Google it）。
68. 如何守护您的基础架构，网络和运行的应用程序？
69. 了解如何设置、配置和使用某些监控系统（Nagios，Zabix，Sensu，Prometheus ...）。
70. 阅读有关开源以及如何为开源项目做出贡献的信息，欲了解更多信息：[http：//jvns.ca/blog/2016/10/26/a-few-questions-about-open-source/](http://jvns.ca/blog/2016/10/26/a-few-questions-about-open-source/)。
71. 如果您的系统出现问题，您应该能够进行反思总结改进。使用文档详细记录出现问题的方法，以及我们如何防止再次发生错误。
72. 尝试学习 StackOverflow 的专家如何解决任何问题。永远记住，这是不断变化的技术而不是基础不变的。基础知识总是保持不变。
73. 让 Google，StackOverflow，Quora 等专业论坛成为您的朋友。
74. 尝试建立良好的开发实践和可靠的架构。
75. 了解如何在生产环境进行扩展。
76. 关注开源项目（Kubernetes / Docker 等）或者让您感到兴奋的事情。
77. 在邮件列表/公共论坛/技术聚会上提出问题/疑问/问题并从中学习。
78. 关注来自社区的志同道合的人，并了解最新的技术趋势。
79. 关注一些体面的科技公司工程博客（我们遵循：Google / Uber / Quora / Github / Netflix）。这是您可以直接从专家那里学习的地方，并有机会看到他们解决任何问题的方法。
80. 浏览一些聚合资讯，如Reddit，黑客新闻，媒体等。
81. 在 twitter 上关注志同道合的开发人员和技术公司。（我总是阅读文章和观看会议/会议，反思总结是我最喜欢的内容。我也会跟进着一些 Github repo 看看我使用的技术发生了什么。）
82. 阅读各种与技术相关的博客并订阅 DevOps Newsletters。
83. 如果可能的话，参加当地的聚会和会议。您将有机会从资深人仕和其他人那里学到很多东西。
84. 了解可伸缩性和高度分布式系统。如何让它们始终保持运行状态？
85. 最后但并非最不重要，阅读书籍。

如果您拥有大部分技能，则可以确保您具备 DevOps，SRE 和系统工程师的能力条件。

你无法一次性学习所有这些，但拥有正确的心态是重要的。即使熟悉所有这些也肯定需要时间。你可能会失败很多次，从你的错误中吸取教训，不要重蹈覆辙。

永远记住，我们都是学习者。我们通过推敲和试验来学习。失败时不要气馁，因为这是我们学习的方式。

我们很乐意听取您的建议，将其归类并添加到此列表中。

