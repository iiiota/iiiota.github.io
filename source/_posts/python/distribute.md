---
title: distribute
date: 2025-05-30 00:44:50
tags:
  - Python
  - distribute
categories:
  - [ Python ]
---


> `distutils` 是 Python 标准库的原始构建和分发系统。虽然直接使用 `distutils` 正在逐步淘汰，但它仍然为当前的打包和分发基础架构奠定了基础，仍然是标准库的一部分。
> `setuptools` 作为 `distutils` 的取代者，能够声明对其他包的依赖。
> `wheel` 是一个将 `bdist_wheel` 命令添加到 distutils/setuptools 的项目。产生一个跨平台的二进制打包格式（轮子文件）。允许在系统上安装Python库，甚至包括二进制扩展的库，而不需在本地进行构建。


# 分发

安装当前推荐的构建和分发工具：

```shell
python -m pip install setuptools wheel twine
```

# 打包

[https://packaging.python.org/en/latest/tutorials/packaging-projects/](https://packaging.python.org/en/latest/tutorials/packaging-projects/)



