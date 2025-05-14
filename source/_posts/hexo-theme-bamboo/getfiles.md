---
title: getfiles
date: 2025-05-15 05:17:53
tags:
  - Bamboo
categories:
  - [Bamboo]
---


# 获取文件

文件必须要在 `source` 目录下。

```
# 指定类型文件
{% getFiles asset/audio, mp3 %}
```

{% getFiles asset/audio, mp3 %}

--------------------

```
# 所有文件
{% getFiles asset %}
```

{% getFiles asset %}

--------------------

```
# 所有文件，自定义图片
{% getFiles asset, '', https://tse3-mm.cn.bing.net/th/id/OIP-C.oGbjgWNX4DBXyKf0P_xOmwHaHa?w=212&h=188&c=7&o=5&dpr=1.24&pid=1.7 %}
```

{% getFiles asset, '', https://tse3-mm.cn.bing.net/th/id/OIP-C.oGbjgWNX4DBXyKf0P_xOmwHaHa?w=212&h=188&c=7&o=5&dpr=1.24&pid=1.7 %}
