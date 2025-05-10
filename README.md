# 同步构建

CloudFlare不会自动拉取submodule来构建项目，需要通过一下命令：

```
git submodule update --remote --recursive
```

CloudFlare构建项目，不能全局安装依赖，package.json中的script应该加上npx执行。

```
  "scripts": {
    "build": "npx hexo generate",
    "clean": "npx hexo clean",
    "deploy": "npx hexo deploy",
    "server": "npx hexo server"
  },
```