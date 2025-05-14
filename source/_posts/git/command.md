---
title: command
date: 2025-05-13 20:56:36
tags:
  - Git
categories:
  - [ Tool, Git]
---


# 命令

## 查看帮助文档

```bash
# 指定命令的帮助
git help CMD
git CMD --help
```


## 查看状态

```bash
# 项目当前状态：所在分支、差异
git status
# 用户信息
git config user.name
git config user.email
# 指向的远程仓库
git remote -v
# 已有的标签
git tag
# 标签的提交信息
git show v1.0
# 指定版本的提交信息
git show 9cf65ab
# 所有自定义的别名
git config --global --get-regexp 'alias\.'
# origin远程仓库信息
git remote show origin
```


## 查看日志

格式占位符：[https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E6%9F%A5%E7%9C%8B%E6%8F%90%E4%BA%A4%E5%8E%86%E5%8F%B2#pretty_format](https://git-scm.com/book/zh/v2/Git-%E5%9F%BA%E7%A1%80-%E6%9F%A5%E7%9C%8B%E6%8F%90%E4%BA%A4%E5%8E%86%E5%8F%B2#pretty_format)

```bash
git log
# 指定提交次数
git log -2
# 详情
git log -1 -p
# 提交统计信息
git log -1 --stat
# 不含merge提交
git log --no-merges
# 内置格式: oneline short full fuller
git log --pretty=oneline
# 自定义格式
git log --pretty=format:"%h - %an, %ar: %s"
# 图形化格式
git log --pretty=format:"%h %s" --graph
# 按时间过滤
git log --since="2 days ago"
# 按作者过滤
git log --author="xxx"
git log --committer="xxx"
```


## 文件操作

```bash
# 默认暂存区和工作区中都移除
git rm '指定模式'            # -f强制
git rm --cached log/\*.log  # 只删暂存区

# 移动文件
git mv FROM TO
```


## 修改、回滚

```bash
# 替换上次的提交
git commit -amend
# 暂存区->工作区
git reset HEAD '文件'
# 用最近提交覆盖
git checkout -- '文件'
# 回滚版本
git reset --hard 版本号
```


## 标签

```bash
# 已有标签
git tag
# 标签的提交信息
git show v1.0
# 打轻量标签，仅为了引用某次提交，没有额外信息
git tag -l 'v1.0'
# 打附注标签 -m：标签信息
git tag -a v1.1 -m "COMMENT"
# 给指定提交打标签
git tag -a v1.2 9cf65ab
# 删除本地标签
git tag -d v1.2
# 删除远程标签
git push origin --delete v1.2
# 推送标签
git push origin v1.2
# 推送所有标签
git push origin --tags
# 切换到标签提交状态，HEAD会分离
git checkout v1.2
```

HEAD分离：
- 含义：不再指向分支，而是指定的提交对象（指定标签/哈希）。
- 风险：HEAD分离状态下的提交不基于分支，无法推送到远程仓库（不可追踪）。
- 应用场景：历史版本的临时验证，若需要基于此修改必须创建新分支。


## 别名

Git支持对命令自定义别名。
```bash
# 切换分支
git config --global alias.co checkout
# 取消暂存
git config --global alias.unstage 'reset HEAD --'
# 最近一次提交
git config --global alias.last 'log -1 HEAD'
# 外部命令别名，!表示外部命令 gitk为git的GUI
git config --global alias.visual '!gitk'
git config --global alias.dir '!dir'

git co master
git unstage FILE
git last
git visual
git dir

# 删除别名
git config --global --unset alias.visual
git config --global --unset alias.dir
```


## 分支

```bash
# 当前分支
git branch
# 分支最近提交
git branch -v
# 查看已合并到当前分支的分支, --no-merged同理
git branch --merged
# 创建分支
git branch dev
# 切换分支, HEAD指向dev
git checkout dev
git checkout dev origin/dev
# 新建并切换分支
git checkout -b fix
# 合并fix分支到当前分支
git merge fix
# 删除分支
git branch -d fix
# 查看所有分支提交历史
git log --oneline --decorate --graph --all
```

## 克隆、拉取

```bash
git clone https://github.com/USERNAME/REPO.git
```

提示：
- origin: 自动指向远程仓库地址。
- master: 指向本地分支的最新提交，或main。
- origin/master: 标记本地master分支的拉取时状态，无法改变。

```bash
# 拉取远程分支，自动合并
git pull
git pull origin dev

# 下载远程有但本地没有的所有信息，不自动合并
git fetch origin
# 必须手动合并
git merge origin
```

提示：
- `git fetch origin` : 协作时，别人的提交可能和本地产生冲突，fetch可以更好的解决冲突。


## 推送

```bash
# 推送到远程仓库
git push origin dev
# 删除远程仓库中的分支
git push origin -d dev

# 删除远程标签
git push origin --delete v1.2
# 推送标签
git push origin v1.2
```


## 变基

详见：[https://git-scm.com/book/zh/v2/Git-%e5%88%86%e6%94%af-%e5%8f%98%e5%9f%ba](https://git-scm.com/book/zh/v2/Git-%e5%88%86%e6%94%af-%e5%8f%98%e5%9f%ba)

和 `merge` 类似，用于整合不同分支的修改。

区别：
- `merge` : 将两分支的最新快照和最近的公共祖先快照进行 **三方合并** ，并生成一个新的快照提交。
- `rebase` : 找到当前分支自最近公共祖先之后的所有修改（提取为临时文件），然后当前分支指向目标分支，再依次应用修改（提交历史更简洁）。

案例：

![basic-rebase-1.png](https://telegraph-image-ydn.pages.dev/api/rfile/basic-rebase-1.png)

```bash
# merge
git checkout master
git merge experiment
```

![basic-rebase-2.png](https://telegraph-image-ydn.pages.dev/api/rfile/basic-rebase-2.png)

```bash
# rebase: experiment分支的修改变基到master上
git checkout experiment
git rebase master
```

![basic-rebase-3.png](https://telegraph-image-ydn.pages.dev/api/rfile/basic-rebase-3.png)

```bash
# 回到master分支，进行一次快进合并
git checkout master
git merge experiment
git push
```

![basic-rebase-4.png](https://telegraph-image-ydn.pages.dev/api/rfile/basic-rebase-4.png)

```bash
# 变基发生冲突时,先解决冲突,再继续
$ git mergetool
$ git rebase --continue
# 利用变基来整合提交
$ git rebase 版本号	# 合并当前到指定版本再提交
$ git rebase HEAD-3	  # 合并当前版本的最近3个版本再提交
```


### 变基风险

如果提交存在于你的仓库之外，而别人可能基于这些提交进行开发，那么不要执行变基。


### cherry-pick

将当前分支的若干提交信息应用到其他分支。

```bash
# 按提交顺序先后应用，会依次生成提交
git cherry-pick HASHCODE
```

应用场景：
> 如本应该在 dev 分支上修改提交的，错误地在 fix 分支上提交了。`cherry-pick` 可以挑选指定提交在 dev 上进行提交。
