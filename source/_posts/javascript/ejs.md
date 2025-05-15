---
title: ejs
date: 2025-05-16 02:44:14
tags:
  - ejs
  - template
categories:
  - [js, ejs]
---


> 嵌入式js，一种简单的模板语言，让你可以通过 `js` 生成 `html` 代码。无需纠结于如何组织内容，无需重新发明迭代和控制流，它只是纯粹的 JavaScript。


# embedded javascript

官网：[https://ejs.co/](https://ejs.co/)
Github：[https://github.com/mde/ejs](https://github.com/mde/ejs)
Playground：[https://ionicabizau.github.io/ejs-playground/](https://ionicabizau.github.io/ejs-playground/)

特性：

- 快速编译、渲染。
- 简单的模板标签 `<% %>` 。
- 自定义分隔符，`[? ?]` 代替 `<% %>` 。
- 可包含子模板。
- 客户端、服务器都支持。
- 中间JavaScript的静态缓存。
- 用Express系统编译。

```ejs
let people = ['geddy', 'neil', 'alex'];
let html = ejs.render('<%= people.join(", "); %>', {people: people});
```


## Tags

标签。

- `<%` : 脚本标签，用于流程控制，无输出。
- `<%_` : 脚本标签，合并前置的所有空白字符。
- `<%=` : 输出值到模板（已转义的HTML）。
- `<%-` : 输出未转义的值到模板。
- `<%#` : 注释标签，不执行，无输出。
- `<%%` : 输出一个字面量 `<%` 。
- `%>` : 纯文本结束标签。
- `-%>` : 裁剪后续空行。
- `_%>` : 合并后续的所有空白字符。


## Includes

引用其他文件。

```html
<ul>
  <% users.forEach(function(user){ %>
    <%- include('user/show', {user: user}); %>
  <% }); %>
</ul>
```
