---
title: exception
date: 2025-05-29 00:43:53
tags:
  - Python
  - Exception
categories:
  - [ Python, Exception]
---


# 异常处理

异常匹配支持同一个类或者基类。

```python
while True:
    try:
        x = int(input("Please enter a number"))
        break
    # 指定一种类型
    except ValueError:
        print("Oops! no valid number)
    # 指定多种类型
    except (RuntimeError, TypeError, NameError):
        pass
```

所有异常都继承自 `BaseException` ，可用作通配符，匹配所有异常。不推荐，容易掩盖真正的编程错误！

```python
import sys

try:
    f = open('myfile.txt')
    s = f.readline()
    i = int(s.strip())
except OSError as err:
    print("OS error: {0}".format(err))
except ValueError:
    print("Could not convert data to an integer.")
except BaseException as err:
    print(f"Unexpected {err=}, {type(err)=}")
    raise
# 必须放在所有 except 子句之后，没有引发异常但又必须要执行的代码
else:
    f.close()
```


## 异常参数

会绑定到一个异常实例并将参数存储在 `instance.args` 中。也可以在引发异常之前先实例化一个异常并根据需要向其添加任何属性。

```python
try:
    raise Exception('spam', 'eggs')
except Exception as inst:
    print(type(inst))
    print(inst.args)
    print(inst)
```


## 触发异常

`raise` ：支持强制触发指定的异常。

```python
# 调用有参构造函数
raise NameError('HiThere')
# 调用无参构造函数
raise ValueError
```

不处理异常,重新触发异常：

```python
try:
    raise NameError('HiThere')
except NameError:
    print('An exception flew by!')
    raise
```


## 异常链

一个未处理的异常发生在 `except` 部分内，它将会有被处理的异常附加到它上面。

```python
try:
    open("database.sqlite")
except OSError:
    raise RuntimeError("unable to handle error")
```

可选 `from` 子句，表明异常是另一个异常的直接后果：

```python
def func():
    raise ConnectionError

try:
    func()
except ConnectionError as exc:
    raise RuntimeError('Failed to open database') from exc

# 异常链中断
try:
    open('database.sqlite')
except OSError:
    raise RuntimeError from None
```


## 自定义异常

异常都应从 Exception 类派生。命名都以 “Error” 结尾，类似标准异常的命名。模块都应该自定义其相关的异常。


### 自定义清理操作

```python
try:
    raise KeyboardInterrupt
# 总是执行
finally:
    print('Goodbye, world!')
```