---
title: class
date: 2025-05-29 04:06:58
tags:
  - Python
  - Class
categories:
  - [ Python, Class]
---

> 类支持多继承

# 类


## 作用域和命名空间

命名空间：

> python的命名空间规则：内置名称集合（内置函数、内置异常等）、模块的全局名称、函数调用的局部名称、对象的属性集合。不同命名空间中的名称之间没有绝对关系。如不同模块中定义的相同函数不会混淆，需要在其前面加上模块名来调用。
> 命名空间是在不同时刻创建的，且拥有不同的生命周期。内置名称命名空间是在python解释器启动时创建的，模块的全局名称是在读取模块定义时创建，函数调用的局部名称是在函数被调用时创建，并在函数返回或抛出异常时被删除，每次递归调用都有自己的局部命名空间。

`nonlocal` ：

> 明特定变量在外层作用域中，并应在外层作用域中重新绑定。

`global` ：

> 用于表明特定变量在全局作用域里，并应在全局作用域中重新绑定

```python
def scope_test():
    def do_local():
        spam = "local spam"

    def do_nonlocal():
        nonlocal spam
        spam = "nonlocal spam"

    def do_global():
        global spam
        spam = "global spam"

    spam = "test spam"
    do_local()
    print("After local assignment:", spam)
    do_nonlocal()
    print("After nonlocal assignment:", spam)
    do_global()
    print("After global assignment:", spam)

scope_test()
print("In global scope:", spam)

'''
After local assignment: test spam
After nonlocal assignment: nonlocal spam
After global assignment: nonlocal spam
In global scope: global spam
'''
```


## 定义

```python
class MyClass:
    # 文档字符串：__doc__属性
    """A simple example class"""
    # 初始化方法
    def __init_(self):
        self.data = []
    def __init(self, data)
        self.data = data
    def func(self):
        print("Hello world")

# 创建类对象，自动调用类的 __init__ 方法
x = MyClass()
y = MyClass([])
```

- 实例对象：对其唯一的唯一操作就是属性引用，包括数据属性和方法。
- 方法对象：引用实例方法后返回的对象，可以保存起来以后调用。

```python
class Dog:
    # 类变量：所有实例共享
    kind = 'canine'

    def __init__(self, name):
        # 实例变量
        self.name = name

d = Dog('Fibo')
e = Dog('Buddy')
d.kind  # canine
e.kind  # canine
d.name  # Fibo
e.name  # Buddy
```


## 继承

类的所有方法都是 `virtual` 的。

```python
class SubClass(BaseClass):
    pass

base = BaseClass()
sub = SubClass()

# 是否为有类继承关系的实例
isinstance(b, BaseClass)	# True
isinstance(s, BaseClass)	# True

# 检查类继承关系
issubclass(SubClass, BaseClass)	# True
```


### 多继承

属性搜索顺序：深度优先、从左到右

```python
class A:
    pass

class B:
    pass

class C(A, B):
    pass
```


## 私有变量

约定：带有一个下划线 `_` 开头的名称应该被当作是 API 的非公有部分 (无论它是函数、方法或是数据成员)。

```python
class MyClass:
    def __init__(self):
        pass
```


## dataclass

类似于 struct 结构体，用于将一些带名称的数据项捆绑在一起。

```python
from dataclasses import dataclass

@dataclass
class Employee:
    name: str
    dept: str
    salary: int

john = Employee('john', 'lab', 1000)
```


## 迭代器

大多数容器对象都可以使用 `for` 语句：

```python
for ele in [1, 2, 3]:
    print(ele)

for ele in (1, 2, 3):
    print(ele)

for key in {'one':1, 'two':2}:
    print(key)

for char in "123":
    print(char)

for line in open("myfile.txt")
    print(line, end=' ')
```

本质上，`for` 语句会在容器对象上调用 `iter()` 方法，返回一个定义了 `__next__()` 方法的迭代器对象，用于逐一访问容器中的元素。元素用尽后，`__next__()` 会引发 `StopIteration` 异常来通知终止 `for` 循环。

```python
class Reverse:
    """迭代器实现"""
    def __init__(self, data):
        self.data = data
        self.index = len(data)
    
    def __iter__(self):
        return self
    
    def __next__(self):
        if self.index == 0:
            raise StopIteration
        self.index = self.index - 1
        return self.data[self.index]

rev = Reverse('spam')
for char in rev:
    print(char)     # m a p s
```


## 生成器

用于创建迭代器的简单而强大的工具。当它们要返回数据时会使用 `yield` 语句。 每次在生成器上调用 `next()` 时，它会从上次离开的位置恢复执行（它会记住上次执行语句时的所有数据值）。 

```python
def reverse(data):
    for index in range(len(data)-1, -1, -1):
        yield data[index]

for char in reverse('spam'):
    print(char)     # m a p s
```

> 用生成器来完成的操作同样可以用基于类的迭代器来完成。 但生成器的写法更为紧凑，因为它会自动创建 `__iter__()` 和 `__next__()` 方法。


## 生成器表达式

类似列表推导式，被设计用于生成器将立即被外层函数所使用的情况。相比完整的生成器更紧凑但较不灵活，相比等效的列表推导式则更为节省内存。

```python
sum(i*i for i in range(10))                 # sum of squares, 285

xvec = [10, 20, 30]
yvec = [7, 5, 3]
sum(x*y for x,y in zip(xvec, yvec))         # dot product, 260

unique_words = set(word for line in page  for word in line.split())
valedictorian = max((student.gpa, student.name) for student in graduates)

data = 'golf'
list(data[i] for i in range(len(data)-1, -1, -1))   # ['f', 'l', 'o', 'g']
```
