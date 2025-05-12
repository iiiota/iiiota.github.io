---
title: setup
date: 2025-05-12 17:49:59
tags: [Hexo]
---


# 创建


## 环境

- Git
- Node.js
- Hexo


## 初始化

```bash
hexo init FOLDER
cd FOLDER
npm install
```

目录结构：
```
.
├── _config.yml
├── package.json
├── scaffolds
├── source
|   ├── _drafts
|   └── _posts
└── themes
```

文件说明：

- **_config.yml** ：大部分都可在此配置。
- **package.json** ：项目基本信息、依赖、脚本等。
- **scaffolds** ：模板文件，创建文件时使用。
- **source** ：用户资源文件夹。
- **themes** ：存放各种主题。
