---
title: template
date: 2025-05-15 01:46:35
tags:
  - Bamboo
categories:
  - [Bamboo]
---

# 模板引擎

## 标题

```
# 标题
{% title h6, 标题%}
{% title h6, 标题, warning %}
{% titleB h6, 标题, red %}
{% titleB h6, 标题, #E2E2E2 %}
```

{% title h6, 标题%}
{% title h6, 标题, warning %}
{% titleB h6, 标题, red %}
{% titleB h6, 标题, #E2E2E2 %}


## pdf

```
# pdf，安装：npm install hexo-pdf
{% pdf  /asset/pdf/test.pdf %}
```

{% pdf  /asset/pdf/test.pdf %}


## 音频

```
{% audio /asset/audio/test.mp3 %}
```

{% audio /asset/audio/test.mp3 %}


## 视频

```
视频，100%宽度
```

{% video /asset/video/test.mp4%}

```
视频，50%宽度
{% videos, 2 %}
{% video /asset/video/test.mp4%}
{% video /asset/video/test.mp4%}
{% endvideos %}
```

{% videos, 2 %}
{% video /asset/video/test.mp4%}
{% video /asset/video/test.mp4%}
{% endvideos %}

```
视频，25%宽度
{% videos, 4 %}
{% video /asset/video/test.mp4%}
{% video /asset/video/test.mp4%}
{% video /asset/video/test.mp4%}
{% video /asset/video/test.mp4%}
{% endvideos %}
```

视频，25%宽度
{% videos, 4 %}
{% video /asset/video/test.mp4%}
{% video /asset/video/test.mp4%}
{% video /asset/video/test.mp4%}
{% video /asset/video/test.mp4%}
{% endvideos %}

## 时间线

```
{% timeline %}

{% timenode 2025-03-03 [1.0.3 -> 1.0.3](https://github.com/) %}
这是一段测试文字。
{% endtimenode %}

{% timenode 2025-02-02 [1.0.2 -> 1.0.2](https://github.com/) %}
1. 这是一段测试文字。
2. 这是一段测试文字。
{% endtimenode %}

{% timenode 2025-01-01 [1.0.0 -> 1.0.0](https://github.com/) %}
- 这是一段测试文字。
- 这是一段测试文字。
{% endtimenode %}

{% endtimeline %}
```

--------------------

{% timeline %}

{% timenode 2025-03-03 [1.0.3 -> 1.0.3](https://github.com/) %}
这是一段测试文字。
{% endtimenode %}

{% timenode 2025-02-02 [1.0.2 -> 1.0.2](https://github.com/) %}
1. 这是一段测试文字。
2. 这是一段测试文字。
{% endtimenode %}

{% timenode 2025-01-01 [1.0.0 -> 1.0.0](https://github.com/) %}
- 这是一段测试文字。
- 这是一段测试文字。
{% endtimenode %}

{% endtimeline %}


## 文本

### 格式

```
{% u 下划线 %}
{% emp 着重号 %}
{% wavy 波浪线 %}
{% del 删除线 %}
{% kbd command %} + {% kbd D %}
{% psw 密码样式的文本 %}
```

{% u 下划线 %}
{% emp 着重号 %}
{% wavy 波浪线 %}
{% del 删除线 %}
{% kbd command %} + {% kbd D %}
{% psw 密码样式的文本 %}

### 颜色

```
{% span yellow, 文本块 %}
{% span info, 文本块 %}
{% span large, 文本块 %}
{% span success small, 文本块 %}
```

{% span yellow, 文本块 %}
{% span info, 文本块 %}
{% span large, 文本块 %}
{% span success small, 文本块 %}

### 填充色

```
{% pbg yellow, 文本块 %}
{% pbg blue, 文本块 %}
{% pbg info, 文本块 %}
{% pbg warning, 文本块 %}
{% pbg danger, 文本块 %}
{% pbg success, 文本块 %}
```

{% pbg yellow, 文本块 %}
{% pbg blue, 文本块 %}
{% pbg info, 文本块 %}
{% pbg warning, 文本块 %}
{% pbg danger, 文本块 %}
{% pbg success, 文本块 %}


### 段落

```
{% p, 文本段落 %}
{% p yellow, 文本段落 %}
{% p primary, 文本段落 %}
{% p info, 文本段落 %}
{% p warning, 文本段落 %}
{% p danger, 文本段落 %}
{% p success, 文本段落 %}
{% p red, 文本段落 %}
{% p green, 文本段落 %}
{% p blue, 文本段落 %}
{% p center, 文本段落 %}
{% p center large danger, 文本段落 %}
{% p center large info, 文本段落 %}
{% p center small, 文本段落 %}
```

{% p, 文本段落 %}
{% p yellow, 文本段落 %}
{% p primary, 文本段落 %}
{% p info, 文本段落 %}
{% p warning, 文本段落 %}
{% p danger, 文本段落 %}
{% p success, 文本段落 %}
{% p red, 文本段落 %}
{% p green, 文本段落 %}
{% p blue, 文本段落 %}
{% p center, 文本段落 %}
{% p center large danger, 文本段落 %}
{% p center large info, 文本段落 %}
{% p center small, 文本段落 %}


## 按钮

```
{% btn 按钮, / %} {% btn warning, 按钮, / %} {% btn info, 按钮, / %}  {% btn success, 按钮, / %}  {% btn danger, 按钮, / %}
{% btn hollow, Github, https://github.com/, fab fa-github %}
{% btn solid, Stackoverflow, https://stackoverflow.com/, fab fa-stack-overflow %}
{% btn large round solid warning, 开始使用, https://baidu.com, fa fa-download %}
{% btn large round solid info, 开始使用, https://baidu.com, fa fa-download %}
{% btn large round solid success, 开始使用, https://baidu.com, fa fa-download %}
{% btn large round solid danger, 开始使用, https://baidu.com, fa fa-download %}
{% btn large solid success, 开始使用, https://baidu.com, fa fa-download %}
{% btn large warning hollow, 开始使用, https://baidu.com, fa fa-download %}
{% btn large info hollow, 开始使用, https://baidu.com, fa fa-download %}
{% btn large success hollow, 开始使用, https://baidu.com, fa fa-download %}
{% btn large danger hollow, 开始使用, https://baidu.com, fa fa-download %}
{% btn success hollow, 开始使用, https://baidu.com, fa fa-download %}
```

{% btn 按钮, / %} {% btn warning, 按钮, / %} {% btn info, 按钮, / %}  {% btn success, 按钮, / %}  {% btn danger, 按钮, / %}
{% btn hollow, Github, https://github.com/, fab fa-github %}
{% btn solid, Stackoverflow, https://stackoverflow.com/, fab fa-stack-overflow %}
{% btn large round solid warning, 开始使用, https://baidu.com, fa fa-download %}
{% btn large round solid info, 开始使用, https://baidu.com, fa fa-download %}
{% btn large round solid success, 开始使用, https://baidu.com, fa fa-download %}
{% btn large round solid danger, 开始使用, https://baidu.com, fa fa-download %}
{% btn large solid success, 开始使用, https://baidu.com, fa fa-download %}
{% btn large warning hollow, 开始使用, https://baidu.com, fa fa-download %}
{% btn large info hollow, 开始使用, https://baidu.com, fa fa-download %}
{% btn large success hollow, 开始使用, https://baidu.com, fa fa-download %}
{% btn large danger hollow, 开始使用, https://baidu.com, fa fa-download %}
{% btn success hollow, 开始使用, https://baidu.com, fa fa-download %}

```
{% btn center large, 百度一下, https://baidu.com, fa fa-download %}
{% btn center large round solid, 开始下载, https://baidu.com, fa fa-download %}
```

{% btn center large, 百度一下, https://baidu.com, fa fa-download %}
{% btn center large round solid, 开始下载, https://baidu.com, fa fa-download %}

```
{% btns circle grid4 %}
  {% cell QQ头像, https://baidu.com, http://q1.qlogo.cn/g?b=qq&nk=1730241541&s=640 %}
  {% cell QQ头像, https://baidu.com, http://q1.qlogo.cn/g?b=qq&nk=1730241541&s=640 %}
  {% cell QQ头像, https://baidu.com, http://q1.qlogo.cn/g?b=qq&nk=1730241541&s=640 %}
  {% cell QQ头像, https://baidu.com, http://q1.qlogo.cn/g?b=qq&nk=1730241541&s=640 %}
{% endbtns %}
```

{% btns circle grid4 %}
  {% cell QQ头像, https://baidu.com, http://q1.qlogo.cn/g?b=qq&nk=1730241541&s=640 %}
  {% cell QQ头像, https://baidu.com, http://q1.qlogo.cn/g?b=qq&nk=1730241541&s=640 %}
  {% cell QQ头像, https://baidu.com, http://q1.qlogo.cn/g?b=qq&nk=1730241541&s=640 %}
  {% cell QQ头像, https://baidu.com, http://q1.qlogo.cn/g?b=qq&nk=1730241541&s=640 %}
{% endbtns %}

```
{% btns rounded grid4 %}
  {% cell 下载源码, /, fa fa-download %}
  {% cell 查看文档, /, fa fa-book %}
  {% cell 下载源码, /, fa fa-download %}
  {% cell 查看文档, /, fa fa-book %}
{% endbtns %}
```

{% btns rounded grid4 %}
  {% cell 下载源码, /, fa fa-download %}
  {% cell 查看文档, /, fa fa-book %}
  {% cell 下载源码, /, fa fa-download %}
  {% cell 查看文档, /, fa fa-book %}
{% endbtns %}


## 进度条

```
{% progress 70 danger 进度条测试 %}
{% progress 60 info 进度条测试 %}
{% progress 60 success 进度条测试 %}
{% progress 60 warning 进度条测试 %}
{% progress 60 primary 进度条测试 %}
{% progress 60 #000 进度条测试 %}
{% progress 60 #2f54eb 进度条测试 %}
```

{% progress 70 danger 进度条测试 %}
{% progress 60 info 进度条测试 %}
{% progress 60 success 进度条测试 %}
{% progress 60 warning 进度条测试 %}
{% progress 60 primary 进度条测试 %}
{% progress 60 #000 进度条测试 %}
{% progress 60 #2f54eb 进度条测试 %}

```
{% progressCircle 70 danger 进度条测试 %}
{% progressCircle 80 info 进度条测试 %}
{% progressCircle 60 success 进度条测试 %}
{% progressCircle 70 #12e9e9 70% %}
{% progressCircle 70 skyblue 70% %}
```

{% progressCircle 70 danger 进度条测试 %}
{% progressCircle 80 info 进度条测试 %}
{% progressCircle 60 success 进度条测试 %}
{% progressCircle 70 #12e9e9 70% %}
{% progressCircle 70 skyblue 70% %}


## 页签栏

```
{% tabs tab-id %}

<!-- tab 栏目1 -->
这是一段测试文字。
<!-- endtab -->

<!-- tab 栏目2 -->
这是一段测试文字。
<!-- endtab -->

{% endtabs %}
```

{% tabs tab-id %}

<!-- tab 栏目1 -->
这是一段测试文字。
<!-- endtab -->

<!-- tab 栏目2 -->
这是一段测试文字。
<!-- endtab -->

{% endtabs %}


## 网站卡片

```
{% sitegroup %}
    {% site 名字, url=http://www.baidu.com, screenshot=https://pic4.zhimg.com/v2-7fcb0d73e1d90788ccf136e22ba7b1bd_r.jpg, avatar=https://pic4.zhimg.com/80/v2-45eb5749949e7f90a5c788f9bc5721ef_1440w.jpg, description=描述 %}
    {% site 名字, url=http://www.baidu.com, screenshot=https://pic4.zhimg.com/v2-7fcb0d73e1d90788ccf136e22ba7b1bd_r.jpg, avatar=https://pic4.zhimg.com/80/v2-45eb5749949e7f90a5c788f9bc5721ef_1440w.jpg, description=描述 %}
    {% site 名字, url=http://www.baidu.com, screenshot=https://pic4.zhimg.com/v2-7fcb0d73e1d90788ccf136e22ba7b1bd_r.jpg, avatar=https://pic4.zhimg.com/80/v2-45eb5749949e7f90a5c788f9bc5721ef_1440w.jpg, description=描述 %}
    {% site 名字, url=http://www.baidu.com, screenshot=https://pic4.zhimg.com/v2-7fcb0d73e1d90788ccf136e22ba7b1bd_r.jpg, avatar=https://pic4.zhimg.com/80/v2-45eb5749949e7f90a5c788f9bc5721ef_1440w.jpg, description=描述 %}
{% endsitegroup %}
```

{% sitegroup %}
    {% site 名字, url=http://www.baidu.com, screenshot=https://pic4.zhimg.com/v2-7fcb0d73e1d90788ccf136e22ba7b1bd_r.jpg, avatar=https://pic4.zhimg.com/80/v2-45eb5749949e7f90a5c788f9bc5721ef_1440w.jpg, description=描述 %}
    {% site 名字, url=http://www.baidu.com, screenshot=https://pic4.zhimg.com/v2-7fcb0d73e1d90788ccf136e22ba7b1bd_r.jpg, avatar=https://pic4.zhimg.com/80/v2-45eb5749949e7f90a5c788f9bc5721ef_1440w.jpg, description=描述 %}
    {% site 名字, url=http://www.baidu.com, screenshot=https://pic4.zhimg.com/v2-7fcb0d73e1d90788ccf136e22ba7b1bd_r.jpg, avatar=https://pic4.zhimg.com/80/v2-45eb5749949e7f90a5c788f9bc5721ef_1440w.jpg, description=描述 %}
    {% site 名字, url=http://www.baidu.com, screenshot=https://pic4.zhimg.com/v2-7fcb0d73e1d90788ccf136e22ba7b1bd_r.jpg, avatar=https://pic4.zhimg.com/80/v2-45eb5749949e7f90a5c788f9bc5721ef_1440w.jpg, description=描述 %}
{% endsitegroup %}


## 单选框

```
{% radio 测试文字。 %}
{% radio red, 测试文字。 %}
{% radio yellow, 测试文字。 %}
{% radio warning, 测试文字。 %}
{% radio checked, 测试文字。 %}
```

{% radio 测试文字。 %}
{% radio red, 测试文字。 %}
{% radio yellow, 测试文字。 %}
{% radio warning, 测试文字。 %}
{% radio checked, 测试文字。 %}


## 复选框

```
{% checkbox 测试文字。 %}
{% checkbox checked, 支持简单的 [markdown](https://guides.github.com/features/mastering-markdown/) 语法 %}
{% checkbox red, 测试文字。 %}
{% checkbox green checked, 绿色 + 默认选中 %}
{% checkbox yellow checked, 黄色 + 默认选中 %}
{% checkbox cyan checked, 青色 + 默认选中 %}
{% checkbox blue checked, 蓝色 + 默认选中 %}
{% checkbox plus green checked, 增加 %}
{% checkbox minus yellow checked, 减少 %}
{% checkbox times red checked, 叉 %}
```

{% checkbox 测试文字。 %}
{% checkbox checked, 支持简单的 [markdown](https://guides.github.com/features/mastering-markdown/) 语法 %}
{% checkbox red, 测试文字。 %}
{% checkbox green checked, 绿色 + 默认选中 %}
{% checkbox yellow checked, 黄色 + 默认选中 %}
{% checkbox cyan checked, 青色 + 默认选中 %}
{% checkbox blue checked, 蓝色 + 默认选中 %}
{% checkbox plus green checked, 增加 %}
{% checkbox minus yellow checked, 减少 %}
{% checkbox times red checked, 叉 %}


## NoteBlock

```
{% noteblock base, 标题（可选） %}
    描述
{% endnoteblock %}

{% noteblock quote, 标题（可选） %}
    描述
{% endnoteblock %}

{% noteblock warning, 标题（可选） %}
    描述
{% endnoteblock %}

{% noteblock success, 标题（可选） %}
    描述
{% endnoteblock %}

{% noteblock danger, 标题（可选） %}
    描述
{% endnoteblock %}

{% noteblock info, 标题（可选） %}
    描述
{% endnoteblock %}
```

{% noteblock base, 标题（可选） %}
    描述
{% endnoteblock %}

{% noteblock quote, 标题（可选） %}
    描述
{% endnoteblock %}

{% noteblock warning, 标题（可选） %}
    描述
{% endnoteblock %}

{% noteblock success, 标题（可选） %}
    描述
{% endnoteblock %}

{% noteblock danger, 标题（可选） %}
    描述
{% endnoteblock %}

{% noteblock info, 标题（可选） %}
    描述
{% endnoteblock %}


## Note

```
> markdown默认写法，描述文字。
{% note warning, 警告描述。 %}
{% note danger, 危险描述。 %}
{% note success, 成功描述。 %}
```

> markdown默认写法，描述文字。


## 链接

```
{% link 点击跳转到百度, http://www.baidu.com, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}

{% link 点击跳转到百度, http://www.baidu.com, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}
```

{% link 点击跳转到百度, http://www.baidu.com, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}

{% link 点击跳转到百度, http://www.baidu.com, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}

```
{% linkgroup %}
{% link 点击跳转到百度, http://www.baidu.com, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}

{% link 点击跳转到百度, http://www.baidu.com, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}

{% link 点击跳转到百度, http://www.baidu.com, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}

{% link 点击跳转到百度, http://www.baidu.com, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}
{% endlinkgroup %}
```

{% linkgroup %}
{% link 点击跳转到百度, http://www.baidu.com, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}

{% link 点击跳转到百度, http://www.baidu.com, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}

{% link 点击跳转到百度, http://www.baidu.com, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}

{% link 点击跳转到百度, http://www.baidu.com, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}
{% endlinkgroup %}


## 图片


### 行内图片
```
# 行内图片
这是 {% inlineimage http://img.doutula.com/production/uploads/image/2019/08/15/20190815849485_fKMqYD.gif %} 一段话。
```

这是 {% inlineimage http://img.doutula.com/production/uploads/image/2019/08/15/20190815849485_fKMqYD.gif %} 一段话。


### 段落图片

```
# 指定宽度
{% image https://pic3.zhimg.com/80/v2-08d7fdf0201e560c22a2e9d9c2c040f6_1440w.jpg?source=1940ef5c, width=400px, alt=自定义名 %}
```

{% image https://pic3.zhimg.com/80/v2-08d7fdf0201e560c22a2e9d9c2c040f6_1440w.jpg?source=1940ef5c, width=400px, alt=自定义名 %}

```
# 指定背景色
{% image  https://pic3.zhimg.com/80/v2-c18a3b0f2e82533d6c47e72e085aca0b_1440w.jpg?source=1940ef5c, width=400px, bg=#1D0C04, alt=自定义背景色 %}
```

{% image  https://pic3.zhimg.com/80/v2-c18a3b0f2e82533d6c47e72e085aca0b_1440w.jpg?source=1940ef5c, width=400px, bg=#1D0C04, alt=自定义背景色 %}


### Gallery图片

```
{% gallery stretch, 4 %}
![图片描述](https://pic2.zhimg.com/80/v2-bcb819edb98e081817066eb6b0e6a2ef_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-f1b467abef1caeb5537f399da4ddbc9d_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-c513cb0d2eff43b5391ea682f1ba07c6_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-bcb819edb98e081817066eb6b0e6a2ef_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-f1b467abef1caeb5537f399da4ddbc9d_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-c513cb0d2eff43b5391ea682f1ba07c6_1440w.jpg?source=1940ef5c)
{% endgallery %}
```

{% gallery stretch, 4 %}
![图片描述](https://pic2.zhimg.com/80/v2-bcb819edb98e081817066eb6b0e6a2ef_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-f1b467abef1caeb5537f399da4ddbc9d_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-c513cb0d2eff43b5391ea682f1ba07c6_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-bcb819edb98e081817066eb6b0e6a2ef_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-f1b467abef1caeb5537f399da4ddbc9d_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-c513cb0d2eff43b5391ea682f1ba07c6_1440w.jpg?source=1940ef5c)
{% endgallery %}


### Gallery图片组合

```
{% gallery %}
![图片描述](https://pic2.zhimg.com/80/v2-bcb819edb98e081817066eb6b0e6a2ef_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-f1b467abef1caeb5537f399da4ddbc9d_1440w.jpg?source=1940ef5c)
{% endgallery %}
{% gallery %}
![图片描述](https://pic2.zhimg.com/80/v2-bcb819edb98e081817066eb6b0e6a2ef_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-f1b467abef1caeb5537f399da4ddbc9d_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-c513cb0d2eff43b5391ea682f1ba07c6_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-c513cb0d2eff43b5391ea682f1ba07c6_1440w.jpg?source=1940ef5c)
{% endgallery %}
{% gallery %}
![图片描述](https://pic2.zhimg.com/80/v2-bcb819edb98e081817066eb6b0e6a2ef_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-f1b467abef1caeb5537f399da4ddbc9d_1440w.jpg?source=1940ef5c)
{% endgallery %}
```

{% gallery %}
![图片描述](https://pic2.zhimg.com/80/v2-bcb819edb98e081817066eb6b0e6a2ef_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-f1b467abef1caeb5537f399da4ddbc9d_1440w.jpg?source=1940ef5c)
{% endgallery %}
{% gallery %}
![图片描述](https://pic2.zhimg.com/80/v2-bcb819edb98e081817066eb6b0e6a2ef_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-f1b467abef1caeb5537f399da4ddbc9d_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-c513cb0d2eff43b5391ea682f1ba07c6_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-c513cb0d2eff43b5391ea682f1ba07c6_1440w.jpg?source=1940ef5c)
{% endgallery %}
{% gallery %}
![图片描述](https://pic2.zhimg.com/80/v2-bcb819edb98e081817066eb6b0e6a2ef_1440w.jpg?source=1940ef5c)
![图片描述](https://pic2.zhimg.com/80/v2-f1b467abef1caeb5537f399da4ddbc9d_1440w.jpg?source=1940ef5c)
{% endgallery %}


### Gallery组

```
<div class="gallery-group-main">
    {% galleryGroup '壁纸' '收藏的一些壁纸' '/gallery/bizhi' https://pic1.zhimg.com/80/v2-23c3820e8abfb1cef689531af2dc6d09_1440w.jpg?source=1940ef5c %}
    {% galleryGroup '古典图片' '中国古典图片' '/gallery/gudian' https://pic1.zhimg.com/80/v2-8d542d68cbbf0e5f503da9e3f72b8447_1440w.jpg?source=1940ef5c %}
    {% galleryGroup '风景' '风景图片' '/gallery/fengjing' https://pic1.zhimg.com/80/v2-56164ef0695767475935c9e019c594ae_1440w.jpg?source=1940ef5c %}
</div>
```

<div class="gallery-group-main">
    {% galleryGroup '壁纸' '收藏的一些壁纸' '/gallery/bizhi' https://pic1.zhimg.com/80/v2-23c3820e8abfb1cef689531af2dc6d09_1440w.jpg?source=1940ef5c %}
    {% galleryGroup '古典图片' '中国古典图片' '/gallery/gudian' https://pic1.zhimg.com/80/v2-8d542d68cbbf0e5f503da9e3f72b8447_1440w.jpg?source=1940ef5c %}
    {% galleryGroup '风景' '风景图片' '/gallery/fengjing' https://pic1.zhimg.com/80/v2-56164ef0695767475935c9e019c594ae_1440w.jpg?source=1940ef5c %}
</div>


## 折叠

### 文本

```
{% folding cyan open, 查看默认打开的折叠框 %}
  这是一个默认打开的折叠框。
{% endfolding %}
```

{% folding cyan open, 查看默认打开的折叠框 %}
  这是一个默认打开的折叠框。
{% endfolding %}

### 列表

```
{% folding yellow, 查看列表测试 %}
  - item1
  - item2
{% endfolding %}
```

{% folding yellow, 查看列表测试 %}
  - item1
  - item2
{% endfolding %}

### 代码

{% folding green, 查看代码测试 %}
```bash
npm install xxx
```
{% endfolding %}

### 图片

```
{% folding 查看图片测试 %}
  {% image https://pic3.zhimg.com/80/v2-08d7fdf0201e560c22a2e9d9c2c040f6_1440w.jpg?source=1940ef5c, width=400px, alt=自定义名 %}
{% endfolding %}
```

{% folding 查看图片测试 %}
  {% image https://pic3.zhimg.com/80/v2-08d7fdf0201e560c22a2e9d9c2c040f6_1440w.jpg?source=1940ef5c, width=400px, alt=自定义名 %}
{% endfolding %}

### 嵌套

```
{% folding red open, 查看嵌套测试 %}
{% folding blue, 查看嵌套测试2 %}
{% folding 查看嵌套测试3 %}
描述文本
<span><img src='https://image.dbbqb.com/202101221115/7cdd741907c2ea150d054d24c4da6594/4d0G' ></span>
{% endfolding %}
{% endfolding %}
{% endfolding %}
```

{% folding red open, 查看嵌套测试 %}
{% folding blue, 查看嵌套测试2 %}
{% folding 查看嵌套测试3 %}
描述文本
<span><img src='https://image.dbbqb.com/202101221115/7cdd741907c2ea150d054d24c4da6594/4d0G' ></span>
{% endfolding %}
{% endfolding %}
{% endfolding %}
