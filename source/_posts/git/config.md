---
title: config
date: 2025-05-13 19:49:52
tags:
  - Git
  - Glob
categories:
  - [ Tool, Git]
---

# Git 配置

详见: [https://git-scm.com/book/zh/v2](https://git-scm.com/book/zh/v2/%E8%B5%B7%E6%AD%A5-%E5%88%9D%E6%AC%A1%E8%BF%90%E8%A1%8C-Git-%E5%89%8D%E7%9A%84%E9%85%8D%E7%BD%AE) 


## git config

```bash
# 查看配置
git config --list --show-origin
git config --list
git config --local user.name
git config --local user.email
```

### 配置继承机制

Git支持配置继承机制。
- `/etc/gitconfig` : 系统级别配置，`--system` 。
- `~/.gitconfig` : 指定用户级别配置，`--global` 。
- `.git/config` : 项目级别配置，`--local` (默认)。


### `.gitignore`

Git支持忽略指定文件/目录，使其不加入版本控制，采用 Glob 匹配。

```
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
.[oa]
~ 
```

> Glob: 一种针对文件路径匹配的正则
> - `#` 注释
> - `/` 目录
> - `**` 任意多中间目录
> - `*` 任意多个字符
> - `?` 单个字符
> - `!` 取反
> - `[]` 其中的单个字符
> - `[! ]` 不在其中的单个字符
> - `[ - ]` 范围内单个字符，数字/字母，`!` 忽略指定模式之外的文件/目录


### 扩展工具

**Beyond Compare** : 可用于 diff/merge，可通过修改配置文件或者命令自定义。
```bash
git config --global diff.tool bc4
git config --global difftool.bc4.cmd \"D:/Beyond Compare 4/BCompare.exe\" \"$LOCAL\" \"$REMOTE\"
git config --global merge.tool bc4
git config --global mergetool.bc4.cmd \"D:/Beyond Compare 4/BCompare.exe\" \"$LOCAL\" \"$REMOTE\" \"$BASE\" \"$MERGED\"
git config --global mergetool.bc4.trustExitCode true
git config --global mergetool.keepBackup false
```

对应配置：
```
[diff]
    tool = bc4
[difftool "bc4"]
    # cmd = \"D:/Beyond Compare 4/BCompare.exe\" \"$LOCAL\" \"$REMOTE\" \"$REMOTE\"
    path = D:/Beyond Compare 4/BCompare.exe
[merge]
    tool = bc4
[mergetool "bc4"]
    # cmd = \"D:/Beyond Compare 4/BCompare.exe\" \"$LOCAL\" \"$REMOTE\" \"$REMOTE\" \"$BASE\" \"$MERGED\"
    path = D:/Beyond Compare 4/BCompare.exe
    trustExitCode = true
[mergetool]
    keepBackup = false
```

使用：
```shell
git difftool HEAD
git mergetool
```