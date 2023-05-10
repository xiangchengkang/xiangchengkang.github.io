---
title: hexo使用
date: 2023-03-23 00:10:29
comments: true #是否可评论 
layout: post # 公开文章 
categories:
	- java
toc: true
coverImg: 
tags: java
top: false
cover: false
img: 
---



:smile:



# 最全示例

```markdown
---
title: typora-vue-theme主题介绍
date: 2018-09-07 09:25:00
author: 赵奇
img: /source/images/xxx.jpg
top: true
cover: true
coverImg: /images/1.jpg
password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
toc: false
mathjax: false
summary: 这是你自定义的文章摘要内容，如果这个属性有值，文章卡片摘要就显示这段文字，否则程序会自动截取文章的部分内容作为摘要
categories: Markdown
tags:
  - Typora
  - Markdown
---
```



https://gitee.com/hx926453/hexo-theme-matery



{% button url, text, icon [class], [title] %}

# 什么是 Hexo？
Hexo 是一个快速、简洁且高效的博客框架。
<!--more-->
Hexo 使用 Markdown（或其他渲染引擎）解析文章，在几秒内，即可利用靓丽的主题生成静态网页。

hexo官网：https://hexo.io/

# 安装hexo
用管理员身份打开cmd输入：npm install hexo-cli -g
输入hexo -version可查看版本信息。

# 新建发布文章（post page）

执行以下命令后会自动在`\myblog\source\_posts`下新建一个`a.md`并且标题是“a”，此时刷新`http://localhost:4000/`可以看到本地已经更新出标题为a的这篇文章。

```java
hexo new a
```

# 新建草稿（draft page）

执行以下命令后会自动在`\myblog\source\_drafts`下新建一个`b.md`并且标题是“b”，此时刷新`http://localhost:4000/`本地并没有更新出这篇文章。

```java
hexo new draft b
```

# 发布草稿

草稿可以通过命令变成发布文章，仍然是需要在根目录执行以下命令

```javascript
hexo publish b
```

这个时候你会发现_drafts里的b.md不见了，跑到了_posts里面,也就说明你的草稿发布成功了。

# 开启服务
hexo server

# 新建文章
hexo new a

# 新建草稿
hexo new draft b

# 发布草稿成为文章
hexo publish b

# 发布关于
hexo new page c

# 生成静态文章
hexo generate 或者是 hexo g
# 部署文章
hexo deploy 或者是 hexo d




title: 我就是标题
date: 2021-09-25 23:32:04
comments: true #是否可评论 
layout: post # 公开文章 
toc: true #是否显示文章目录 
tags:   #标签 
 - 我就是新的标签1
 - 老子是新的标签2





# demo1

demo1德莫demodemo1m

## demo11

```java
# Hexo Configuration
## Docs: https://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site
title: hexoDemo
subtitle: '这是一个demo页'
description: 'hexoDemo用于介绍如何使用hexo'
keywords: 'hexo,node,博客'
author: 项成康
language: zh-CN
# language: en
timezone: ''

# URL
## Set your site url here. For example, if you use GitHub Page, set url as 'https://username.github.io/project'
url: https://xiangchengkang.github.io
permalink: :year/:month/:day/:title/
permalink_defaults:
pretty_urls:
  trailing_index: true # Set to false to remove trailing 'index.html' from permalinks
  trailing_html: true # Set to false to remove trailing '.html' from permalinks

# Directory
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link:
  enable: true # Open external links in new tab
  field: site # Apply to the whole site
  exclude: ''
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  auto_detect: false
  tab_replace: ''
  wrap: true
  hljs: false
prismjs:
  enable: false
  preprocess: true
  line_number: true
  tab_replace: ''

# Home page setting
# path: Root path for your blogs index page. (default = '')
# per_page: Posts displayed per page. (0 = disable pagination)
# order_by: Posts order. (Order by date descending by default)
index_generator:
  path: ''
  per_page: 12
  order_by: -date

# Category & Tag
default_category: uncategorized
category_map:
tag_map:

# Metadata elements
## https://developer.mozilla.org/en-US/docs/Web/HTML/Element/meta
meta_generator: true

# Date / Time format
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss
## updated_option supports 'mtime', 'date', 'empty'
updated_option: 'mtime'

# Pagination
## Set per_page to 0 to disable pagination
per_page: 12
pagination_dir: page

# Include / Exclude file(s)
## include:/exclude: options only apply to the 'source/' folder
include:
exclude:
ignore:

# Extensions
## Plugins: https://hexo.io/plugins/
## Themes: https://hexo.io/themes/
theme: matery

# Deployment
## Docs: https://hexo.io/docs/one-command-deployment
deploy:
  type: 'git'
  repo: https://github.com/xiangchengkang/xiangchengkang.github.io.git
  branch: master

```









