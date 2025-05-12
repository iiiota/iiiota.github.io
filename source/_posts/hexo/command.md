---
title: command
date: 2025-05-12 19:41:16
tags: [Hexo]
---


# 指令


## init

```bash
# 新建一个博客网站项目
hexo init FOLDER
```


## new

**LAYOUT**: 布局，支持draft page post，默认：_config.yml中的default_layout。
**TITLE**: 文章标题，必需的，也会作为目录名，并默认在其下创建index.md。

```bash
# 新建文章
hexo init LAYOUT TITLE
```

选项：
- `--path`: 指定文章路径，`hexo new page --path about/me "About me"` 则生成about/me.md。
- `--replace`: 若存在同名文件是否替换。
- `--slug`: 文章别名，自定义文章url。


## generate

生成静态文件。
```bash
hexo generate
```

选项：
- `--deploy`: 生成后自动部署。
- `--watch`: 监视文件变动。
- `--force`: 强制重新生成。
- `--concurrency`: 同时生成的文件的最大数量，默认无限制。


## publish

发布草稿。
```bash
hexo publish
```


## server

启动服务器。
```bash
hexo server
```

选项：
- `--port`: 指定端口号。
- `--static`: 只使用静态文件。
- `--log`: 启用日志。


## deploy

部署网站。
```bash
hexo deploy
```

选项：
- `--generate`: 在部署前生成。


## render

渲染文件。
```bash
hexo render FILE
```

选项：
- `--output`: 输出目标地址。


## migrate

从其他博客系统迁移。
```bash
hexo migrate TYPE
```


## clean

清理缓存文件。
```bash
hexo clean
```


## list

列出所有路由。
```bash
hexo list TYPE
```


## version

显示版本信息。
```bash
hexo version
```

## config

列出网站_config.yml配置。
```bash
# 指定了KEY，则只展示对应值
# 同时指定KEY&VALUE，则表示修改
hexo config KEY VALUE
```


## 选项

```bash
# 显示草稿（source/_drafts）
hexo --draft
```