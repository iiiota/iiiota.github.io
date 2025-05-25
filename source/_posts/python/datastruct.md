---
title: datastruct
date: 2025-05-25 23:23:46
tags:
  - Python
  - DataStruct
categories:
  - [ Python, DataStruct ]
---

> 数据结构，集合。

## List

列表。

```python
l = []
tmp = [2, 3]
# 末尾追加元素，[1]，相当于 l[len(l):] = [1]
l.append(1)
# 末尾合并列表，[1, 2, 3]，相当于 l[len(l):] = tmp
l.extend(tmp)
# 指定位置插入元素，[0, 1, 2, 3]
l.insert(0, 0)
# 移除一个指定元素，[0, 1, 2]，未找到则抛出ValueError异常
l.remote(3)
# 移除最后一个元素，[0, 1]
l.pop()
# 查找元素的首个索引，1，未找到则抛出范围
l.index(1)
# 统计指定元素出现的次数，1
l.count(0)
# 排序，默认从大到小
l.sort()
# 清空列表，相当于 del a[:]
l.clear()
# 翻转列表
l.reverse()
# 浅拷贝，相当于 a[:]
l.copy()
```


### List 实现 Stack

```python
stack = [3, 4, 5]
stack.append(6)		# 入栈
stack.pop()			# 出栈
```


### List 实现 Queue

```python
from collections import deque
queue = deque([3, 4, 5])
queue.append(6)		# 入队
queue.popleft()		# 出队
```


### List Comprehensions

列表推导式。

```python
# [0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
[x**2 for x in range(10)]
# 等效于：
aar = []
for x in range(10):
    aar.append(x**2)

# [(1, 2), (1, 3), (2, 1), (2, 3), (3, 1), (3, 2)]
[(x, y) for x in [1,2,3] for y in [1,2,3] if x != y]
# 等效于：
aar = []
for x in [1,2,3]:
    for y in [1,2,3]:
        if x != y:
            aar.append((x, y))
            
# [(1, 0), (1, 2), (1, 3), (3, 0), (3, 1), (3, 2)]
[(x, y) for x in range(4) if x%2 != 0 for y in range(4) if x != y]
# 等效于
for x in range(4):
    if x%2 != 0:
        for y in range(4):
            if x != y:
                aar.append((x,y))
```


### 嵌套的列表推导式

```python
       
# 嵌套函数
from math import pi
# ['3.1', '3.14', '3.142', '3.1416', '3.14159']
[str(round(pi, i)) for i in range(1, 6)]

# 嵌套列表
matrix = [
    [1,2,3,4],
    [5,6,7,8],
    [9,10,11,12],
]
reverse = [[row[i] for row in matrix] for i in range(4)]
# 等价于：
aar = []
for i in range(4):
    tmp = []
    for row in matrix:
        tmp.append(row[i])
    aar.append(tmp)
    

# 遍历index value
for i, v in enumerate(aar):
    print(i, v)
    
# 多个list合并匹配
questions = ['name', 'quest', 'favorite color']
answers = ['lancelot', 'the holy grail', 'blue']
for q, a in zip(questions, answers):
    print('What is your {0}?  It is {1}.'.format(q, a))
```


## Del

按照索引移除元素或切片。

```python
arr = [1, 2, 3, 4, 5]
del arr[0]      # [2, 3, 4, 5]
del arr[1,3]	# [2, 4]
del arr[:]      # []
del arr			# 删除整个变量
```


## Truple

```python
t0 = ()
t1 = 1, 2, 3	# 元组打包
t2 = (4, 5, 6)

# 可嵌套
t3 = t1, t2		# ((1, 2, 3), (4, 5, 6))
# 不可变的
t3[0] = 999		# TypeError

t4 = 'hello',	# ('hello',) 单元素的元组
x, y, z = t1	# 元组解包，必须一一对应
```


## Set

不重复元素的无序容器。

```python
nums = {1, 2, 3}	# 初始化集合
nums = set()		# 初始化空集合 nums={}为字典
1 in nums			# 判断是否在set中

nums1 = set('helloworld')	# {'l', 'e', 'r', 'o', 'd', 'w', 'h'}
nums2 = set('word')			# {'l', 'r', 'd', 'o', 'w'}
nums1 - nums2				# 差集 {'e', 'h'}
nums1 | nums2				# 并集 {'l', 'e', 'r', 'o', 'd', 'w', 'h'}
nums1 & nums2				# 交集 {'l', 'r', 'd', 'o', 'w'}
nums1 ^ nums2				# 出去交集部分 {'e', 'h'}

# 集合推导式
{ x for x in nums if x not in nums1 }	# {'e', 'h'}
```


## Dictionary

key通常是字串或数字，或不可变类型(元组)，但引用可变对象的元组不可作为key。

```python
dic = {}						# dict()
dic = {'name':'sb', 'age':18}
dic = dict(sape=4139, guido=4127, jack=4098)
dic = dict([('sape', 4139), ('guido', 4127), ('jack', 4098)])

dic['age'] = 20

[*dic]							# ['name', 'age']
sorted(dic)						# {'name': 'sb', 'age': 18}
dic = {x: x**2 for x in (2, 4, 6)}	# {2: 4, 4: 16, 6: 36}
```


## 循环技巧

循环遍历字典：

```python
dic = {'gallahad': 'the pure', 'robin': 'the brave'}
# 遍历key value
for k, v in dic.items():
    print(k, v)
```

循环序列：

```python
# 遍历index value
for i, v in enumerate(list):
    print(i, v)
```

循环两个或多个序列，一一匹配：

```python
questions = ['name', 'quest', 'favorite color']
answers = ['lancelot', 'the holy grail', 'blue']
for q, a in zip(questions, answers):
    print('What is your {0}?  It is {1}.'.format(q, a))
```

逆向对序列循环：

```python
for i in reversed(range(1, 10, 2)):
    print(i)
```

指定顺序循环序列：

```python
basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
for i in sorted(basket):
    print(i)
```

循环序列唯一元素：

```python
basket = ['apple', 'orange', 'apple', 'pear', 'orange', 'banana']
for f in sorted(set(basket)):
    print(f)
```


## 序列比较

两个相同序列类型之间可以进行比较，采用 字典式 顺序对元素一一对应比较。

```python
(1, 2, 3) < (1, 2, 4)					# True
[1, 2, 3] < [1, 2, 4]					# True
(1, 2)    < (1, 2, -1)					# True
'ABC' < 'C' < 'Pascal' < 'Python'		# True
(1, 2, ('aa', 'ab'))   < (1, 2, ('abc', 'a'), 4)	# True
```
