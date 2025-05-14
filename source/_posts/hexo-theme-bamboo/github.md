---
title: github
date: 2025-05-15 04:28:39
tags:
  - Bamboo
  - Github
categories:
  - [Bamboo]
---

# Github


## 卡片

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


## issues-timeline

会去拿到某个repo仓库的issue内容，用 `timeline` 标签的形式显示。

### github

```
{% issues timeline | api=https://api.github.com/repos/USERNAME/REPO/issues?sort=updated&state=closed&page=1&per_page=10 %}
```

{% folding 查看Github issues %}
  {% issues timeline | api=https://api.github.com/repos/jiangrui1994/CloudSaver/issues?sort=updated&state=closed&page=1&per_page=10 %}
{% endfolding %}

### gitee

```
{% issues timeline | api=https://gitee.com/api/v5/repos/y_project/RuoYi/issues %}
```

{% folding 查看Gitee issues %}
  {% issues timeline | api=https://gitee.com/api/v5/repos/y_project/RuoYi/issues %}
{% endfolding %}

### issue api

```
{% linkgroup %}
    {% link github的开放api, https://docs.github.com/cn/rest/overview/resources-in-the-rest-api, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}
    {% link gitee的开放api, https://gitee.com/api/v5/swagger#/getV5ReposOwnerRepoIssues, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}
{% endlinkgroup %}
```

{% linkgroup %}
    {% link github的开放api, https://docs.github.com/cn/rest/overview/resources-in-the-rest-api, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}
    {% link gitee的开放api, https://gitee.com/api/v5/swagger#/getV5ReposOwnerRepoIssues, https://cdn.pixabay.com/photo/2018/12/05/13/41/panda-3857754__340.jpg %}
{% endlinkgroup %}


## issues-sites

会去拿到某个repo仓库的issue内容，用sites标签的形式显示，可用作友链功能，都适用于 `github` `gitee` 。

issue需要包含数据：
```json
{
    "title": "",
    "url": "",
    "avatar": "",
    "screenshot": "",
    "description": ""
}
```

### github

```
{% issues sites | api=https://api.github.com/repos/yuang01/friends/issues?sort=updated&state=open&page=1&per_page=4&labels=active %}
```

{% issues sites | api=https://api.github.com/repos/yuang01/friends/issues?sort=updated&state=open&page=1&per_page=4&labels=active %}

### gitee

```
{% issues sites | api=https://gitee.com/api/v5/repos/yuang01/friends/issues?sort=updated&state=open&page=1&per_page=4&labels=active %}
```

{% issues sites | api=https://gitee.com/api/v5/repos/yuang01/friends/issues?sort=updated&state=open&page=1&per_page=4&labels=active %}

### 分组显示

```
{% issues sites | api=https://api.github.com/repos/yuang01/examples/issues?sort=updated&state=open&page=1&per_page=100 | group=version:版本：v3.0,版本：v2.0 %}
```

{% issues sites | api=https://api.github.com/repos/yuang01/examples/issues?sort=updated&state=open&page=1&per_page=100 | group=version:版本：v3.0,版本：v2.0 %}
