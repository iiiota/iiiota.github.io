---
title: submodule
date: 2025-05-14 02:37:11
tags:
  - Git
categories:
  - [ Tool, Git]
---


# 子模块


## 克隆

```bash
# 克隆主模块，仅包含子模块的引用
git clone add https://github.com/USERNAME/REPO.git

# 再克隆子模块
git submodule init
git submodule update --recursive

# 同时克隆主模块及其子模块
git clone https://github.com/USERNAME/REPO.git --recursive
```


## 添加

```bash
# 拉取子模块
git submodule add https://github.com/USERNAME/SUBREPO.git mymodule
git push
```

说明：
- 拉取子模块，会新建 `.gitmodule` 文件（存储模块路径和仓库地址）、`mymodule` 目录（关联子模块项目）。
- 本地仅引用子模块，指向一个特定的哈希提交，和分支无关。


## 更新

```bash
# 进入子模块目录拉取
cd mymodule
git pull
git push

# 批量更新子模块
git submodule foreach git pull
# 提交最新引用的子模块
git push
```

## 删除

git并没有直接提供对应的命令。

```bash
# 从暂存区中移除
git rm cached mymodule
# 从工作区中移除
rm rf mymodule
# 删除子模块配置
rm .gitmodules
# 提交
git add .
git commit -m 'remote submodule'
git push
```


## 修改

主模块和子模块是独立的，主模块中应该仅可修改主模块中的内容，对子模块仅进行更新。
