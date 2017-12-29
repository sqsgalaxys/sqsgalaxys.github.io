---
title: Use CMD
date: 2016-08-08 17:48:56
update:
tags: [Use,CMD]
---

# 使用 CMD 
## 使用 CMD 查看端口占用情况并结束占用的程序 
查看所有的端口占用情况
`netstat -an0`
查看指定端口的占用情况
`netstat -an0|findstr "4000"`
<!-- more -->
查看PID对应的进程
`tasklist|findstr "1234"`
结束进程
`taskkill /f /t /im ***.exe`
## 参考：
- [windows 如何查看端口占用情况? - Windows - language - ITeye论坛](http://www.iteye.com/topic/1117270 "")

----
## `tasklist` 命令
- [Tasklist](https://technet.microsoft.com/en-us/library/bb491010.aspx "")
