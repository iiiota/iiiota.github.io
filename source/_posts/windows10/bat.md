---
title: bat
date: 2025-05-14 12:07:25
tags:
  - Bat
categories:
  - [ Windows10, Bat]
---


# Bat脚本

参考：[https://zhuanlan.zhihu.com/p/523558706](https://zhuanlan.zhihu.com/p/523558706)


## 注释

注释信息

```bat
@rem ############
@rem   始终不打印
@rem ############

rem -------------
rem @echo on时才打印
rem -------------

:: **************
:: @rem的简写形式
:: **************
```


## 回显

```bat
:: 关闭回显
echo off
:: 打开回显
echo on
:: 关闭当前命令回显
@echo CMD
:: 输出空行
echo .
:: 打印提示
echo MY_MSG
:: 重定向
echo "MY_MSG" > FILE
```


## 暂停

```bat
:: 暂停执行，任意键继续
pause
:: 暂停执行，修改暂停提示
@echo CONTINUE... & pause > nul
```


## 环境变量

`%ENV_VAR%`

```bat
:: Windows_NT
echo %OS%
:: 当前目录
echo %CD%
```


## 状态码

表示上条语句是否成功执行，0成功，非0错误。

```bat
echo %errorlevel%
```


## 预定义变量

```bat
:: 输出传入参数，%*为参数列表
echo %1 %2
:: 当前目录
echo %CD%
:: 当前日期
echo %DATE%
:: 当前时间
echo %TIME%
:: 随机数0-32767
echo %RANDOM%
```


## 自定义变量

```bat
:: 声明变量
set str1=hello_world
:: 提示输入来赋值
set /p str2=请输入字串
:: 可进行数值运算
set num=99
set /a num=num+1
echo %num%
```


## 执行bat脚本

```bat
:: 等待返回才继续执行
call BAT_FILE [PAREMS]
:: 直接继续执行本程序
start BAT_FILE [PAREMS]
```


## 字符串

```bat
:: 替换截取
set str=hello_world
:: 前5个字符 hello
echo %str:~0,5%
:: 最后5个字符 world
echo %str:~-5%
echo %str:~6%
:: o_w
echo %str:~4,-4%

:: 替换
echo %str:world=bat%

:: 拼接
echo %str%%str%
```


## 时间操作

```bat
:: 当前日期
echo %date%
:: 当前时间
echo %time%
:: 自定义日期时间格式 2022-01-01 14:25:10
echo %date:~0,4%-%date:~5,2%-%date:~8,2% %time:~0,8%
```


## 窗口自定义设置

```bat
:: 窗口标题
title MY_TITLE

:: 输出颜色
color /?
color 0A

:: 中文编码
chcp 65001
```
