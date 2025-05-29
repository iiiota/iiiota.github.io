---
title: stdlib
date: 2025-05-29 10:49:03
tags:
  - Python
  - Stdlib
categories:
  - [ Python, Stdlib]
---


# 标准库


## 内置命令

```python
import os

# 返回模块内定义的所有名称的字典
dir(os)
# 返回模块的docstring手册
help(os)
```


## 操作系统

```python
import os

# 当前工作目录
os.getcwd()
# 修改当前工作目录
os.chdir('/server/logs')
# 运行shell命令
os.system('mkdir test')
```


## 文件通配符

```python
import glob

# 搜索匹配  文件列表
glob.glob('*.py')
```


## 命令行参数

`python demo.py one two three`

```python
# demo.py
import sys

print(sys.argv)
# ['demo.py', 'one', 'two', 'three']
```

`python top.py --lines=5 alpha.txt beta.txt`

```python
# 提供更复杂的机制处理命令行参数
import argparse

parser = argparse.ArgumentParser(
    prog='top',
    description='Show top lines from each file')
parser.add_argument('filenames', nargs='+')                 # 添加filenames变量：['alpha.txt', 'beta.txt']
parser.add_argument('-l', '--lines', type=int, default=10)  # 添加lines变量：5，默认值10
args = parser.parse_args()
print(args)
```


## 错误重定向&程序终止

sys模块具有 `stdin` `stdout` `stderr` 属性。

```python
import sys

# 错误输出
sys.stderr.write()
# 终止
sys.exit()
```


## 字符串模式匹配

```python
import re
re.findall(r'\bf[a-z]*', 'which foot or hand fell fastest') # ['foot', 'fell', 'fastest']

re.sub(r'(\b[a-z]+) \1', r'\1', 'cat in the the hat')       # 'cat in the hat'
```


## 数学

```python
import math

math.cos(math.pi / 4)
math.log(1024, 2)
```

随机数

```python
import random

random.choice(['apple', 'pear', 'banana'])

random.sample(range(100), 10)
random.random()       # 随机浮点数
random.randrange(6)   # 随机 range(6)
```

统计属性

```python
import statistics

data = [2.75, 1.75, 1.25, 0.25, 0.5, 1.25, 3.5]
statistics.mean(data)       # 均值
statistics.median(data)     # 中位数
statistics.variance(data)   # 方差
```


## 互联网访问

```python
# 从URL检索数据
from urllib.request import urlopen
with urlopen('http://worldtimeapi.org/api/timezone/etc/UTC.txt') as response:
    for line in response:
        line = line.decode()             # Convert bytes to a str
        if line.startswith('datetime'):
            print(line.rstrip())         # Remove trailing newline


# 发送邮件
import smtplib
server = smtplib.SMTP('localhost')
server.sendmail('soothsayer@example.org', 'jcaesar@example.org',
"""To: jcaesar@example.org
From: soothsayer@example.org

Beware the Ides of March.
""")
server.quit()
```


## 日期&时间

```python
from datetime import date

now = date.today()
now
now.strftime("%m-%d-%y. %d %b %Y is a %A on the %d day of %B.")

# dates support calendar arithmetic
birthday = date(1964, 7, 31)
age = now - birthday
age.days
```


## 数据压缩

常用模块：`zlib` `gzip` `bz2` `lzma` `zipfile` `tarfile` 。

```python
import zlib

s = b'witch which has which witches wrist watch'
len(s)  # 41
t = zlib.compress(s)
len(t)  # 37
zlib.decompress(t)
zlib.crc32(s)
```


## 性能测量

`timeit` 精细度较低，`profile` `pstats` 提供了用于较大代码块中识别关键部分的工具。

```python
from timeit import Timer

Timer('t=a; a=b; b=t', 'a=1; b=2').timeit()
Timer('a,b = b,a', 'a=1; b=2').timeit()
```


## 质量控制

为每个函数编写测试。

`doctest` 模块提供了一个工具，用于扫描模块并验证程序文档字符串中嵌入的测试。

```python
def average(values):
    """Computes the arithmetic mean of a list of numbers.

    >>> print(average([20, 30, 70]))
    40.0
    """
    return sum(values) / len(values)

import doctest
doctest.testmod()   # automatically validate the embedded tests
```

`unittest` 模块不像 `doctest` 模块那样易于使用，但它允许在一个单独的文件中维护更全面的测试集。

```python
import unittest

class TestStatisticalFunctions(unittest.TestCase):

    def test_average(self):
        self.assertEqual(average([20, 30, 70]), 40.0)
        self.assertEqual(round(average([1, 5, 7]), 1), 4.3)
        with self.assertRaises(ZeroDivisionError):
            average([])
        with self.assertRaises(TypeError):
            average(20, 30, 70)

unittest.main()  # Calling from the command line invokes all tests
```