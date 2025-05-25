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
import fibo.py
```
