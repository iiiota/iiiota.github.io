---
title: config
date: 2025-05-12 18:05:19
tags: [Hexo]
---


# 配置

Hexo默认提供配置文件：**_config.yml** ，也支持指定为其他配置文件。


## 网站

```yml
title: 网站标题
subtitle: 网站副标题
description: 网站描述
keywords: 网站关键字，支持多个
author: 网站作者
language: zh-CN     # 语言
timezone: ''        # 时区，默认当前电脑时区
```


## 网址

```yml
url: http://iiiota.github.io    # 网址
root: /                         # 网站根目录
permalink: :year/:month/:day/:title/    # 永久链接
permalink_defaults:                     # 永久链接中各部分的默认值
  post: post
pretty_urls:                    # 改写永久链接来美化
  trailing_index: true          # 是否保留尾部的index.html
  trailing_html: true           # 是否保留尾部的.html
```


## 搜索

需要安装插件：`npm install hexo-generator-search --save`

配置：
```yml
search:
  path: search.xml
  field: post
```


## 目录

```yml
source_dir: source              # source文件夹名
public_dir: public              # 生成静态站点的文件夹名
tag_dir: tags                   # 标签文件夹
archive_dir: archives           # 归档文件夹
category_dir: categories        # 分类文件夹
code_dir: downloads/code        # Include code文件夹，在source_dir下
i18n_dir: :lang                 # 国际化文件夹
skip_render:                    # glob匹配到的文件不渲染，而是原样复制到public_dir中
```


## 文章

```yml
new_post_name: :year-:month-:day-:title.md  # 新文章名的格式
default_layout: post        # 默认布局
titlecase: false            # 标题为titlecase，首字母大写
external_link:
  enable: true              # 新页签中打开链接
  field: site               # 应用于整个site, post则仅对文章生效
  exclude: ''               # 需要剔除的子域名
filename_case: 0            # 文件名格式，1:小写 2:大写
render_drafts: false        # 是否显示草稿
post_asset_folder: false    # 启用资源文件夹
relative_link: false        # 链接是否为相对根目录的相对地址
future: true                # 显示未来的文章
syntax_highlighter: highlight.js    # 代码块高亮设置，内置支持highlight.js、prismjs
highlight:
  line_number: true
  auto_detect: false
  tab_replace: ''
  wrap: true
  hljs: false
prismjs:                            # 代码块设置
  preprocess: true
  line_number: true
  tab_replace: ''

search:
  path: search.xml
  field: post

permalink_pinyin:
  enable: true
  separator: '-'
```


## 首页设置

```yml
index_generator:
  path: ''              # 索引页面根路径
  per_page: 10          # 每页文章数
  order_by: -date       # 默认按日期降序，默认：-date
  pagination_dir:       # url格式，默认：page
```


## 分类&标签

```yml
default_category: uncategorized     # 默认分类
category_map:           # 分类别名
tag_map:                # 标签别名
```

案例：
```yml
category_map:
  "yesterday's thoughts": yesterdays-thoughts
  "C++": c-plus-plus
```


## 日期&时间格式

Hexo使用 Monent.js 来解析和显示时间。
```yml
date_format: YYYY-MM-DD
time_format: HH:mm:ss
updated_option: false       # 用于控制Front Matter中没有指定updated时的取值，支持：mtime date empty
```


## 分页

```yml
per_page: 10                # 分页大小，0则关闭，默认：10
pagination_dir: page        # URL格式，默认：page
```


## 扩展

```yml
theme: hexo-theme-bamboo    # 当前主题，false则关闭主题
theme_config:               # 主题配置文件，会覆盖主题中的配置
deploy:                     # 部署相关配置
meta_generator: true        # 是否在html Header中插入标签

ignore:                     # 忽略的文件/目录
feed:
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
  order_by: -date
```


## 文件包含/忽略

glob匹配。
```yml
include:        # 包含文件/目录，仅应用于source目录中
exclude:        # 排除文件/目录，仅应用于source目录中
ignore:         # 忽略文件/目录，应用于所有文件夹
```


## 代替配置文件

自定义配置文件的路径。
```bash
hexo server --config custom.yml
hexo server --config custom.yml,custom2.json
```


## 代替主题配置文件

Hexo主题项目有一个独立的配置文件：_config.yml，可以在博客项目根目录的 _config.yml 中进行配置。

**theme_config**
```yml
# _config.yml
theme: "MY_THEME"       # 指定主题
theme_config:
  bio: "XXX"
  foo:
    bar: "XXX"
```

**_config.[theme].yml**: 放于项目根目录下，并在_config.yml中引用。
