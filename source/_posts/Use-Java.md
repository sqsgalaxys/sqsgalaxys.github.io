---
title: Use Java
date: 2016-08-07 16:03:27
update:
tags: [Use,Java]
categories:
---

'javac' 不是内部或外部命令，也不是可运行的程序
或批处理文件。


<!-- more -->

## Java 获得内存信息或操作内存的接口

// 虚拟机内存系统接口
`MemoryMXBean`

// 虚拟机内存管理器接口
`MemoryManagerMXBean`

// 虚拟机中的内存池接口
`MemoryPoolMXBean`

// 操作系统信息接口
`OperatingSystemMXBean`

----
## java 数据库相关的一些类

```
DbProc dbobj = new DbProc();
Connection conn = dbobj.connect();
Statement stm = conn.createStatement();
ResultSet rst = stm.executeQuery(strSQL);
```

----
## java 文件位置的输入
```
File f=new File("d:\\txdjava\\java12.txt");
File f=new File("d:/txdjava/java12.txt");
```
### 参考:
- [java 中文件路径的表示 - ohuan的日志 - 网易博客](http://hbohuan.blog.163.com/blog/static/2084898200763132748377/ "")
----

----

## java 与 xml 文件

----

----

## java 官方文档
- [The Java™ Tutorials](http://docs.oracle.com/javase/tutorial/ "")
- [The Java® Language Specification](http://docs.oracle.com/javase/specs/jls/se8/html/index.html "")
- [Overview (Java Platform SE 8 )](http://docs.oracle.com/javase/8/docs/api/index.html "")
### 参考:
[技术的正宗与野路子 - 张铁蕾 - 掘金专栏](http://gold.xitu.io/post/57ab4bd32e958a0066cf7041 "")
----

