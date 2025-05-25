---
title: style
date: 2025-05-21 00:41:25
tags:
  - Python
  - Style
categories:
  - [ Python ]
---


## Languge Rules


### Lint

[https://google.github.io/styleguide/pylintrc](https://google.github.io/styleguide/pylintrc)


### Import

使用 `import` 语句导入 package、module ，而不是单独的类型、类、函数。

> 优点：每个标识符都以统一的方式指定。`x.obj`：对象 `obj` 定义在模块 `x` 中。
> 缺点：模块名可能冲突，有些模块名会很长而不方便使用。

```python
# 导入package、module
import x
# x是package的前缀，y是module名（无前缀）
from x import y
# 用于：y模块名冲突、y与公共api的参数名冲突、y模块名太长、y在当前上下文常用。
from x import y as z
```


### Package

使用模块的完整路径名位置导入每个模块。

> 优点：避免以不期望的模块搜索路径而产生的模块名冲突。
> 缺点：使部署代码更加困难，因为必须复制包层次结构。对于现代部署机制来说，这并不是一个真正的问题。

```python
# Yes: 完整路径名
import absl.flags
from doctor.who import jodie
_FOO = absl.flags.DEFINE_string(...)

# Yes: 常见，仅模块名
from absl import flags
from doctor.who import jodie
_FOO = flags.DEFINE_string(...)

# No
import jodie
```


### Exception

异常是允许的，但必须谨慎使用。

> 优点：正常操作代码的控制流不受错误处理代码的干扰。允许控制流在特定条件发生时跳过。
> 缺点：可能导致控制流混乱。在调用库时容易忽略错误情况。

```python
# Yes: 优先使用对应的内置异常，不要使用assert语句代替条件或验证前提条件。
def connect_to_next_port(self, minimum: int) -> int:
    """Connects to the next available port.

    Args:
      minimum: A port value greater or equal to 1024.

    Returns:
      The new minimum port.

    Raises:
      ConnectionError: If no available port is found.
    """
    if minimum < 1024:
      # Note that this raising of ValueError is not mentioned in the doc
      # string's "Raises:" section because it is not appropriate to
      # guarantee this specific behavioral reaction to API misuse.
      raise ValueError(f'Min. port must be at least 1024, not {minimum}.')
    port = self._find_next_open_port(minimum)
    if port is None:
      raise ConnectionError(
          f'Could not connect to service on port {minimum} or higher.')
    # The code does not depend on the result of this assert.
    assert port >= minimum, (
        f'Unexpected port {port} when minimum was {minimum}.')
    return port

# No
def connect_to_next_port(self, minimum: int) -> int:
    """Connects to the next available port.

    Args:
      minimum: A port value greater or equal to 1024.

    Returns:
      The new minimum port.
    """
    assert minimum >= 1024, 'Minimum port must be at least 1024.'
    # The following code depends on the previous assert.
    port = self._find_next_open_port(minimum)
    assert port is not None
    # The type checking of the return statement relies on the assert.
    return port
```

> library package 应该定义自己的异常，必须继承已存在的异常类。异常名以 `Error` 结尾。
> 不用捕获所有的 `except:` 或 `Excetion` 或 `StandardError` 语句。除非重新抛出异常，或者抑制异常重新抛出导致崩溃。
>> `except:` 会捕获所有异常，包括拼写错误的名字、`sys.exit()` 调用、`Ctrl+C` 中断、单元测试失败以及你不想捕获的各种其他异常。
> 尽量最小化 `try/except` 的代码量。`try` 主体越大，越容易抛出异常，并更容易隐藏真正的错误。
> 使用 `finally` 块执行代码，而不论是否抛出异常。对于处理关闭文件等清理工作非常有用。


### Mutable Global State

需要避免可变全局状态。

> 打破封装：这样的设计会使有效的目标难以实现。
> 有可能在导入期间更改模块行为，因为对全局变量的赋值是在模块首次导入时完成的。


### Nested/Local/Inner Classes and Functions

类可以在方法、函数或类中定义。函数可以在方法或函数中定义。嵌套函数对外围作用域中定义的变量具有只读访问权限。

> 优点：允许定义仅在限定作用域生效的工具类和方法。
> 缺点：内部函数和类不能直接被测试，使得外部方法更长更不易读。

不要嵌套函数只是为了对模块的用户隐藏它。相反，应该在模块级别为其名称加上前缀，以便测试仍然可以访问它。

### Comprehensions & Generator Expressions

推导式和生成器表达式。`List` `Dict` `Set` 都提供了这种方式来创建容器类型和迭代器，而无需使用传统的 loops map() filter() lambda 。


