---
title: setup
date: 2025-05-14 02:17:14
tags:
  - Git
categories:
  - [ Tool, Git]
---

# 创建

## 初始化Git项目

```bash
# 初始化（生成.git目录）
git init
# 设置个人信息
git config user.name "xxx"
git config user.email "xxx.@github.com"

# 关联远程仓库
git remote add origin https://github.com/USERNAME/REPONAME.git

# 添加本地文件
touch README.md
git add .
# 
```