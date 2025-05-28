---
title: module
date: 2025-05-26 00:14:17
tags:
  - Python
  - Module
categories:
  - [ Python, Module]
---

# 模块

模块中可包含 函数定义 和 语句，语句只会在首次导入模块时执行！

```python
# fibo.py
def fib(n):    # write Fibonacci series up to n
    a, b = 0, 1
    while a < n:
        print(a, end=' ')
        a, b = b, a+b
    print()

def fib2(n):   # return Fibonacci series up to n
    result = []
    a, b = 0, 1
    while a < n:
        result.append(a)
        a, b = b, a+b
    return result
```

```python
# 只是将模块名称fibo引用进来，而不是其中的函数直接添加进来。
import fibo
# 导入所有不以下划线（_）开头的名称，不推荐
from fibo import *
# 重命名导入名称
import fibo as fib
from fibo import fib as fibonacci
```


## 脚本方式执行模块

```shell
python fibo.py <arguments>
```

`__name__` 赋值为 `__main__`，，模块作为主程序执行，相当于在fibo.py模块末尾添加：

```python
if __name__ == "__main__":
    import sys
    fib(int(sys.argv[1]))
```


## 模块搜索路径

模块搜索优先级：
1. 内置模块
2. `sys.path` ：脚本所在目录（命令行运行）、`PYTHONPATH`（环境变量）、`site-packages`（site模块处理）


## 已编译的python文件

为了快速加载模块，Python会将已编译版本缓存在 `__pycache__` 目录。如 `__pycache__/spam.cpython-33.pyc` ，可使不同python版本编译的模块共存。


## dir() 函数

用于查找所有类型的名称（变量、模块、函数...），返回结果为已排序的字符串列表。

```python
import fibo, sys
dir()       # 当前已定义的名称
dir(fibo)
dir(sys)
```

`dir()` 不会列出内置函数和变量的名称（定义在标准模块 builtins 中）：

```python
import builtins
dir(builtins)
```


## Package-包

如一下文件结构：
```
sound/
  __init__.py
  formats/
    __init__.py
    auread.py
    auwrite.py
  effects/
    __init__.py
    echo.py
    reverse.py
  filters/
    __init__.py
    vocoder.py
```

必须包含 `__init__.py` 文件，才能让python将包含该文件的目录当作包来处理。可以是一个空文件，也可以在其中执行一些初始化设置。

从 `package` 中导入单个 `module` ：

```python
import sound.effects.echo
from sound.effects import echo
from sound.effects.echo import echofilter
```


### 从包中导入 `*`

```python
from sound.effects import *
```

不会把所有子模块都导入到当前命名空间。只确保 `sound.effects` 中定义的名称被导入。除非在 `__init__.py` 中指定了 `__all__` 变量来显式指定 `*` 要导入的模块。

```python
# __init__.py
__all__ = ["echo", "reverse"]
```


### 相对导入

`sound.filters.vocoder` 模块中使用 `sound.effects.echo` 模块。

```python
# 绝对导入
from sound.effects import echo
# 相对导入
from ..effects import echo
```

注意，相对导入基于当前模块名。因为主模块名永远是 "__main__" ，所以如果计划将一个模块用作 Python 应用程序的主模块，那么该模块内的导入语句必须始终使用绝对导入。


### 多目录中的包

`package` 还支持 `__path__` 属性，在包的 `__init__.py` 执行前，`__path__` 被初始化为一个字符串列表，仅包含一个字符串，即 `__init__.py` 所在的目录名称。可以修改此变量来改变此包中搜索模块和子包的方式。