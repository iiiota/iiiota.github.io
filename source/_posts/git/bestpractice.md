---
title: best practice
date: 2025-05-14 02:33:06
tags:
  - Git
categories:
  - [ Tool, Git]
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


## 变基

- 不要在 `master` / `main` 分支上 rebase，这是默认分支。
- 总是在本地分支上 rebase，没有推送到远程仓库，不会影响协作。