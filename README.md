# DevOps China Community Website

Hugo site souce code.

* mv cname to static folder
* setup private repo on gitlab

### 文章规范的一些说明（基于 Markdown 语法）：

1. 所有的英文跟中文之间要有一个空格，英文与标点符号不需要空格；
2. 中文破折号统一使用6个“-”连接；
3. 文中有关代码或可执行命令注意要使用代码块标识符；
4. 文中小标题使用 4 个“#”，文中次标题使用 5 个 “#”；
5. 文中有关链接以 Markdown 标准形式输出；
6. 标题和内容，内容和图片等，均需前后空一行；
7. 文中图片引入均使用 `img` 标签,便于 web 响应式浏览。
8. 翻译文章第一段的译者和出处说明可以用一个 > 开头，每一行的最后加两个空格站位，然后在按会车换行，下面的连续几行都这么操作，就自然换行了；



#### Blog 文章分类

可选分类和解释

* 文档
* 翻译
* 调查
* DevOps
* AIOps
* 
* 


#### Blog 文章标签

可选用得标签和说明

* 
* 
* 
* 



### 关于整理翻译组的译文的说明：

1. 本地同步云端仓库（repo）：

建议每次更新 repo 前都应先同步仓库最新的文件，避免提交时发生冲突。

```bash
$ cd devopschina-web/
$ git fetch & git pull
```
2. 创建对应的 `.md` 文件(以“[UI/UX设计指南：术语、说明、技巧与趋势](https://devopschina.org/blog/ui-ux-design-guide-with-terms-explanations-tips-and-trends/)”为例)：

```bash
$ hugo new content/blog/ui-ux-design-guide-with-terms-explanations-tips-and-trends.md
```
3. 编辑`ui-ux-design-guide-with-terms-explanations-tips-and-trends.md`文件：

`hugo new` 命令初始化得到的 `.md` 文件内容如下：
```yaml
---
title: "Test Draft Blog"
date: 2021-02-24T13:01:21+08:00
draft: true
description: "替换成：120个字符以内的文章内容描述" #共搜索引擎索引使用
bgImage: "images/backgrounds/blog-bg.jpg" # 每个 postTpye 使用一张特定的图片
bgImageAlt: "背景头图名称"
image: "images/blog/ui-ux-001.png" # 图片规格 比例 2*1 ， 推荐 1000px*500px （宽*高）
author: "译者"
postType: "翻译" # 见类型清单，翻译文章由翻译小组定
type: "post"
summary: "页面上：100 字符以内的引导短语"
categories: # 见分类清单，翻译文章由翻译小组定
  - "翻译"
tags: # 可选标签清单，不多于 5 个已有标签，增加标签，需要提交 issue ，小组讨论
  - "UI"
  - "UX"
---
```

需要将该部分改为如下格式，主要是修改为中文标题和新增其它参数，如下：

```yaml
title: "UI/UX 设计指南：术语、说明、技巧与趋势"
date: 2019-11-13T10:14:50+08:00
description: "大家知道，设计决定了大多数软件产品的成功。而软件开发拓展了把设计用于不同产品的新方式。我谈论的是关于网页和应用的设计。没有时尚元素和易用性，就没有伟大的App。功能和吸引力的最优组合可以用来衡量应用的有效性。视觉传达必须简单、直观和吸引人" #共搜索引擎索引使用
bgImage: "images/backgrounds/blog-bg.jpg" # 每个 postTpye 使用一张特定的图片
bgImageAlt: "ALT-txt"
image: "images/blog/ui-ux-001.png" # 图片规格 比例 2*1 ， 推荐 1000px*500px （宽*高）
author: "王国良"
postType: "翻译" # 见类型清单，翻译文章由翻译小组定
type: "post"
summary: "完整的 UI/UX 设计指南，新人可以借之入门，老人可以借之梳理体系。"
categories: # 见分类清单，翻译文章由翻译小组定
  - "翻译"
tags: # 可选标签清单，不多于 5 个已有标签，增加标签，需要提交 issue ，小组讨论
  - "UI"
  - "UX"
---
```

>#### 补充关键字段说明：
>
>1. `draft`：草稿标识，正式发布需删除该标识；
>2. `description`:文章描述，用于浏览器抓取信息；
>3. `bgImage`：文章内容的大背景图；
>4. `image`：列表页文章标题图；
>5. `author`：一般为翻译者或文章作者；
>6. `postType`：发布文章附属类别；
>7. `summary`：该部分为列表页文章推荐语部分；
>8. `categories`：文章类别，翻译、文档、演讲等自定义；
>9. `tags`：文章归类标签，使用多个时采用列表标签形式。

4. 文章内容编排：

具体的编排格式可以参考[src/content/blog/ui-ux-design-guide-with-terms-explanations-tips-and-trends.md](src/content/blog/ui-ux-design-guide-with-terms-explanations-tips-and-trends.md)或其它文章的格式。

5. 本地发布预览

本地编排完文章后，需要在本地借助 `hugo` 生成本地测试服务来检查新增文件的预览效果，如果没问题就可以 `push` 到仓库，每一次 `push` 都会自动发布到正式网站上。

- 本地启动调式命令：

```bash
$ cd src/
$ hugo server -D     # hugo 服务会监听在本地 1313 端口上运行
```
- 本地浏览器预览：

浏览器打开[http://localhost:1313](http://localhost:1313)。

- 同步至仓库：

```bash
$ git fetch & git pull
$ git add .
$ git commit -m "add a xxxxx to blog"
$ git push
```

- 查看 Coding.net 中的构建和部署流水线

https://devopscoach.coding.net/p/devopschina-web/ci/job

如果最近一次触发的构建和部署没有失败的话，删除浏览器缓存，准备检查网站上正式上线的版本。

- 在官网上正式检查部署后的结果

访问[https://devopsmeetup.com/blog/](https://devopsmeetup.com/blog/)检查是否发布成功，并将该文 URL 发回微信群，让微信组负责运营的同学进行公众号编排。

