---
title: Format
date: 2025-05-28 23:17:19
tags:
  - Python
  - Format
categories:
  - [ Python, Format]
---


# 格式化

```python
# 字符串插值
year = "2018"
cur = f'current year is {year}'
cur = f'current year is {year!s}'   # !s:str() !r:repr() !a:ascii()
cur = f'current {year=}'            # current year='2018'

# format方法
yes_votes = 42_572_654
no_votes = 43_132_495
percentage = yes_votes / (yes_votes + no_votes)
'{:-9} YES votes  {:2.2%}'.format(yes_votes, percentage)    # ' 42572654 YES votes  49.67%'
'{0}, {1}'.format('Hello', "World")
'{action}, {target}'.format(action='Hello', target='World')

# str repr
str(year)       # '2018'
repr(year)      # "'2018'"  适于解释器执行的值
```


