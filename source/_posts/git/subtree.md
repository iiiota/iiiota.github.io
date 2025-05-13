---
title: subtree
date: 2025-05-14 03:33:35
tags:
  - Git
categories:
  - [ Tool, Git]
---


# Subtree

**Git更加推荐使用**，和 `submodule` 类似，都是为了解决子模块和主模块之间的关联。`submodule` 出现较早，存在一些弊端：

- 主模块中无法修改子模块代码，必须在子模块中修改提交，再由主模块更新。
- 没有直接删除子模块的命令，需要组合git操作和文件操作进行删除。


## 拉取

```bash
# 增加一个新的远程库
git remote add SUBTREE-ORIGIN https://github.com/USERNAME/SUBTREE.git
git remote show

# 将SUBTREE-ORIGIN远程库的master分支拉取到SUBTREE_FOLDER目录下
git subtree add --prefix=SUBTREE_FOLDER SUBTREE-ORIGIN master --squash
git push
```

- `--squash` : 将依赖仓库的若干合并为一次提交，从而简化主仓库的提交日志。

> `--squash` : 合并为一次提交后，主仓库的引用和依赖仓库没有共同祖先，无法推送到依赖仓库了。 解决方法：push到依赖仓库的一个新分支上，再由依赖仓库来合并到master上（工作流比较麻烦）。
> 
> 不添加 `--squash` : git会将依赖仓库的提交依次合并到主仓库（每次合并都会自动提交一次），这样会污染主仓库的提交日志。

最佳实践：
- `--squash` : 合并/提交要么每次都不用，要么每次都用。

## 更新

```bash
# 同理，pull
git subtree pull --prefix=SUBTREE_FOLDER SUBTREE-ORIGIN master --squash
git push
```


## 修改

不仅可修改主仓库的代码，还可修改依赖仓库的代码并提交。

```bash
# 推送主仓库和依赖仓库的代码修改到主仓库
git pull
# 推送依赖仓库的代码修改到依赖仓库（以--squash合并的则会提交失败）
git subtree push --prefix=SUBTREE_FOLDER SUBTREE-ORIGIN master
git push
```

## 切割

将主仓库中的一部分代码切割出来作为独立的一部分。

> 手动进行剪切不可取，会丢失历史提交信息。

```bash
# 会把其中的文件所有相关提交记录都统计出来
git subtree split --prefix=SUBTREE_FOLDER SUBTREE-ORIGIN master
```

## 日志

```bash
# 主仓库日志
git log
# 依赖仓库日志
git log SUBTREE-ORIGIN
```
