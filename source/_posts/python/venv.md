---
title: venv
date: 2025-05-29 22:07:00
tags:
  - Python
  - pip
  - venv
categories:
  - [ Python]
---

> 应用程序通常会使用不在标准库内的软件包和模块。有时需要特定版本的库，因为可能需要修复特定的错误，或者可以使用库的过时版本的接口编写应用程序。意味着一个版本可能无法满足每个应用程序的要求。
> 解决方案：创建一个 `virtual environment`，一个目录树，其中安装有特定Python版本，以及许多其他包。不同的应用将可以使用不同的虚拟环境。

# 虚拟环境

创建和管理虚拟环境的模块称为 `venv` 。通常会安装可用的最新版本python 或 指定版本。

```shell
# 创建
python -m venv .venv
# 激活
.venv/Scripts/activate.bat
```


## pip

安装、升级和移除软件包。默认 `pip` 从 [https://pypi.org/](https://pypi.org/) 安装软件包。

```shell
# 最新版本
python -m pip install novas
# 指定版本
python -m pip install requests==2.6.0
# 最小版本
python -m pip install "requests>=2.6.0"
# 更新到最新版本
python -m pip install --upgrade requests
# 卸载包
python -m pip uninstall requests
# 查看包信息
python -m pip show requests
# 列出所有包信息
python -m pip list
# 列出已安装的包列表到文件
python -m pip freeze > requirements.txt
# 批量安装包
python -m pip install -r requirements.txt
```



