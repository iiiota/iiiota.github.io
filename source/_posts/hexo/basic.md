---
title: basic
date: 2025-05-12 20:16:00
tags: [Hexo]
---


# 基本操作


## 写作

创建新文章或页面。
```bash
# 布局默认为post，也可提供自己的布局
hexo new LAYOUT TITLE
```


### 布局

Hexo有三种默认布局，不同布局创建的文件会保存在不同路径。
- **post**: source/_posts
- **page**: source
- **draft**: source/_drafts


### 文件名

Hexo默认以文章标题名作为文件名，也可以通过 _config.yml 中的 new_post_name 自定义。
- **:title**: 标题，小写
- **:year**: 创建年份
- **:month**: 创建月份
- **:i_month**: 创建月份，无前导0
- **:day**: 创建日期
- **:i_day**: 创建日期，无前导0


### 草稿

Hexo默认不显示草稿，可通过 `--draft` 来渲染草稿。
```bash
# 发布草稿
hexo publish LAYOUT TITLE
```


### 脚手架

Hexo会根据 `scaffolds` 目录下对应的文件来新建文章。
```bash
# 尝试寻找 photo.md 模板
hexo new photo "MYPHOTO"
```

模板文件中可使用变量：
```yml
---
title: {{ title }}      # 标题
date: {{ date }}        # 创建日期
layout:                 # 布局
tags:                   # 标签
---
```


## 前言

```yml
---
title: TITLE            # 标题
layout:                 # 布局，默认config.default_layout
date: XXX               # 创建日期
updated: XXX            # 更新日期
comments: true          # 是否开启评论功能
tags:                   # 标签支持多个，[]
categories:             # 分类
permalink:              # 覆盖文章的永久链接，以/或.html结尾
except:                 # 
lang:                   # 语言
published:              # 文章是否发布
---
```


### 标签

仅文章支持，可有多个，表示相同层次结构。
```yml
---
tags:
  - Injury
  - Fight
  - Shocking
---
```

或者
```yml
---
tags: [Hexo, Test]
---
```


### 分类

仅文章支持，可有多个，同时复合多层次结构才会汇总显示。
```yml
---
categories:
  - [Sports, Baseball]
  - [MLB, American League, Boston Red Sox]
  - [MLB, American League, New York Yankees]
---
```

或者
```yml
categories:
  - Sports
  - Baseball
```