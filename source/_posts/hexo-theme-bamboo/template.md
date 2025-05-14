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


## 选择框

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


## Github卡片


### 单张卡片

```
{% ghcard iiiota %}
```

{% ghcard iiiota %}


### 表格卡片

```
| {% ghcard iiiota %} | {% ghcard iiiota, theme=vue %} |
| -- | -- |
| {% ghcard iiiota, theme=buefy %} | {% ghcard iiiota, theme=solarized-light %} |
| {% ghcard iiiota, theme=onedark %} | {% ghcard iiiota, theme=solarized-dark %} |
```

| {% ghcard iiiota %} | {% ghcard iiiota, theme=vue %} |
| -- | -- |
| {% ghcard iiiota, theme=buefy %} | {% ghcard iiiota, theme=solarized-light %} |
| {% ghcard iiiota, theme=onedark %} | {% ghcard iiiota, theme=solarized-dark %} |


### 项目卡片

```
{% ghcard iiiota/hexo-theme-bamboo %}
{% ghcard iiiota/hexo-theme-bamboo %}
```

{% ghcard iiiota/hexo-theme-bamboo %}
{% ghcard iiiota/hexo-theme-bamboo %}
