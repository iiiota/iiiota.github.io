---
title: best practice
date: 2025-05-14 02:33:06
tags:
  - Git
categories:
  - [ Tool, Git]
top: true 
---


# 最佳实践

## 初始化远程仓库

前提：需要在 github 中设置好账号或仓库的公钥。

- 推送新建仓库

```bash
# 初始化
git init
git config user.name "USERNAME"
git config user.email "XXX@github.com"
# 本地提交
touch README.md
git add README.md
git commit -m "init"
# 关联远程仓库并提交
git remote add origin git@github.com:USERNAME/REPO.git
git push -u origin master
git remote show origin
```

- 推送已存在仓库

```bash
# 关联远程仓库并提交
git remote add origin git@github.com:USERNAME/REPO.git
git push -u origin master
git remote show origin
```


## 比较差异

```
# 工作区修改
git diff
git diff FILE_NAME

# 暂存区修改
git diff --cached
git diff --staged

# 提交版本
git diff HASH_VALUE

# 指定文件指定提交的差异
git diff HASH_VALUE FILE_NAME
```


## 变基

- 优先选择 `merge` 。
- 不要在 `master` / `main` 分支上 rebase，这是默认分支。
- 总是在本地分支上 rebase，在远程也有的分支上进行 `rebase` 很可能会影响协作。


## 依赖仓库

推荐使用 `subtree` ，而不是 `submodule` 。

- `submodule` : 仅保存子模块的引用而不保存其代码，无法修改提交到子模块仓库，未提供直接删除子模块的命令。
- `subtree` : 主仓库会克隆一份依赖仓库代码，可对主仓库和依赖仓库进行修改提交。

```bash
# 添加依赖仓库
git remote add SUBTREE-ORIGIN https://github.com/USERNAME/SUBTREE.git
git remote show
git subtree add --prefix=SUBTREE_FOLDER SUBTREE-ORIGIN master --squash
git push

# 拉取依赖仓库
git subtree pull --prefix=SUBTREE_FOLDER SUBTREE-ORIGIN master --squash
# 推送依赖仓库修改到依赖仓库
git subtree push --prefix=SUBTREE_FOLDER SUBTREE-ORIGIN master
# 切割部分代码来作为新的依赖仓库（会统计所有相关提交信息）
git subtree split --prefix=SUBTREE_FOLDER SUBTREE-ORIGIN master
# 依赖仓库日志
git log SUBTREE-ORIGIN
```

## 误提交

`cherry-pick` 的目标场景用于处理本应在其他分支上进行的误提交。

```bash
# 按提交顺序先后应用，会依次生成提交
git cherry-pick HASHCODE
```