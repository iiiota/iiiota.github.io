---
title: front-matter
date: 2025-05-15 05:09:39
tags:
  - Bamboo
categories:
  - [Bamboo]
---


# 前言

针对一整篇文章的设置参数，例如

```
---
title: front-matter
date: 2025-05-15 05:09:39
swiper: true                # 文章是否放入轮播图中
swiperImg: '/medias/1.jpg'  # 文章在轮播图中的图片，可以是本地图片或也http://xxx图片
img: '/medias/1.jpg'        # 文章图片，可以是本地图片或也http://xxx图片
tags:
  - Bamboo
categories:
  - [Bamboo]
top: true                   # 是否显示在首页置顶栏
---
```

| 配置选项   | 默认值                      | 描述                                                         |
| ---------- | --------------------------- | ------------------------------------------------------------ |
| title      | `Markdown` 的文件标题        | 文章标题，强烈建议填写此选项                                 |
| date       | 文件创建时的日期时间          | 发布时间，强烈建议填写此选项，且最好保证全局唯一  
| swiper     | false                       | 表示该文章是否需要加入到首页轮播封面中
| swiperImg  | 无                       | 表示该文章在首页轮播封面需要显示的图片路径，如果没有，则默认使用文章的特色图片
| swiperDesc  | 无                       | 表示该文章在首页轮播封面需要显示的文字描述（摘要），如果没有，则使用`excerpt`，如果`excerpt`也没有，则取文章内容
| img        | 无                          | 文章特征图，该文章显示的图片，没有则默认使用文章的特色图片
| excerpt        | 无                          | 文章描述（摘要），该文章在首页的描述文字，如果没有，则取`swiperDesc`,如果`swiperDesc`也没有，则取文章内容（优先取`<!-- more -->`上面的内容）
| top        | false                       | 将该值设为true，则将该篇文章显示在首页的置顶栏目中
| toc        | true                       | 将该值设为false，则该篇文章不显示右侧目录
| tocOpen    | true                       | 将该值设为false，则该篇文章右侧目录默认收缩 
| onlyTitle        | false                       | 文章详情页头部是否只显示标题，不显示日期等信息
| comments   | true                       | 将该值设为false，则该篇文章不显示评论 
| share   | true                       | 将该值设为false，则该篇文章不显示分享按钮
| copyright   | true                       | 将该值设为false，则该篇文章不显示版权声明
| donate   | true                       | 将该值设为false，则该篇文章不显示打赏按钮
| bgImg   | -                       | 单独为这篇文章设置背景图片或者背景颜色，可以是数组，数组里面放图片链接，可以是字符串，字符串里面是颜色值，空值则背景颜色透明 
| bgImgTransition   | fade        | 该篇文章的bgImg设置为数组,该值表示背景图片切换的动画, 有三种值（fade, scale, translate-fade）
| bgImgDelay   | 180000(三分钟)        | 该篇文章的bgImg设置为数组,该值表示背景图片切换的延迟时间, 
| categories | 无                          | 文章分类，本主题的分类表示宏观上大的分类，只建议一篇文章一个分类 | 
| prismjs | 无                          | 如果使用的是hexo自带的prismjs代码高亮，通过设置该值为该篇文章设置不同的代码高亮主题（default, coy, dark, funky, okaidia, solarizedlight, tomorrow, twilight） |
| tags       | 无                          | 文章标签，一篇文章可以多个标签  
| mathjax       | false                          | mathjax公式
| imgTop       | true                | 设置为`false`则文章和自定义页面顶部不要图片
