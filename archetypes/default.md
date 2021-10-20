---
title: "{{ replace .Name "-" " " | title }}"
date: {{ .Date }}
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

