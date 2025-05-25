---
title: basic
date: 2025-05-21 00:18:40
tags:
  - Python
  - Basic
categories:
  - [ Python ]
---


## 流程控制


### if

```python
x = 1
if x < 0:
  print('x less than zero')
elif x == 0:
  print('x equil zero')
else
  print('x great than zero')

a = [1, 2, 3]
if 1 in a:      # 对应 not in
  pass
if a is a:      # 是否为同一对象，对应 not is
  pass
if 1 < 2 > 0:   # 1<2 and 2>0
  pass
if a[0] := 0:   # 先赋值，再使用
  pass
```


### while

```python
x, b = 0, 1
while a < 10:
  print(a)
  a, b = b, a+b
```


### for

```python
words = ['Hello', 'world']
for w in words:
  print(w, len(w))

for i in range(5)   # [0, 4]
  print(i)

for i in range(len(words))
  print(i)
else                # for中未发生break时执行
  print('not break')
```


### Match

类似switch-case，3.10版本特性。

```python
def http_error(s):
  match s:
    case 400:
      return "Bad request"
    case 401 | 402:
      return "Not allowed"
    case _:
      return "something wrong"
        
class point:
  x:int
  y:int
def where_is(point):
  match point:
    case (0, 0):
      print("origin")
    case (0, y):
      print(f"Y={y}")
    case (x, y):
      print(f"X={x}, Y={y}")
    case _:
      print("Not a point")

def where_is(point):
  match point:
    case Point(x=0, y=0):
      print("origin")
    case Point(x=0, y=y):
      print(f"Y={y}")
    case Point():
      print("somewhere else")
    case _:
      print("Not a point")
```


### Pass

充当语句的占位，不执行任何操作。

```python
while True:
  pass

class EmptyClass:     # 常用于创建一个最小的类
  pass

def EmptyFunc(*args): # 函数的占位符
  pass

if True:
  pass
```


### Function

函数没有 `return` 语句时，则默认返回 `None`。

- 默认值参数

```python
def f(a, L=None):
    if L is None:
        L = []
    L.append(a)
    return L

f(1)
f(1, L=[])
```

- 可变参数

```python
# *为元组，**为字典，元组必须位于字典前
def f(a, *args, **kvs):
    """docstring"""
    pass

# a:"H", args:["E","LL","O"], kvs:{"name":"sb"}
f("H", "E", "LL", "O", name="world")
```

- 特殊参数

```python
# / * 仅使得代码已读
def f(pos1, pos2, /, std1, std2, *, kw1, kw2):
    pass
# / 前的参数：仅可按位置传入
# * 前的参数：位置 或 关键字传入
# * 后的参数：仅可按关键字传入

def f1(pos):
    pass
f1(1)
f1(pos=1)

def f2(pos, /):
    pass
f2(1)
f2(pos=2)	# X

def f3(*, kw)
f3(1)		# X
f3(kw=2)
```

- 实参解包

```python
args = [3, 6]
l = list(range(*args))

# 实参位于字典中
def f(name, age):
    pass
args = {"name":"sb", "age":18}
f(**args)
```

- Lambda表达式，用于创建匿名函数

```python
def f(n):
    return lambda x: x+n
```

