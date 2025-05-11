# 主题作为子模块添加

```
touch .gitmodules
git submodule add https://github.com/yuang01/hexo-theme-bamboo.git themes/hexo-theme-bamboo
```

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

并且CloudFlare中的构建命令中也不能直接执行hexo命令，应该替换为`npm run build`来执行package.json中定义的命令。