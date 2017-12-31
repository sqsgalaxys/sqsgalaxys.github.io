---

title: Use-Vim
date: 2016-08-06 19:59:45
tags: [Use,Vim]

---

# vim 使用

----

## 1. 删除文件中所有的空行 :
`:g/^$/d`
<!-- more -->
### 参考:
- [如何在vim中删除空行-Shell-ChinaUnix.net](http://bbs.chinaunix.net/thread-510754-1-1.html "")

----

## 2. 整行移动 :
- 移动到下一行开头
`+`
- 移动到上一行开头
`-`
- 移动到行首
`0`
- 移动到行尾
`$`

---- 

## 3. 符号 `.` :
- 重复命令
- 当前行 `.-1` 代表当前行的上一行

----

## 4. MiniBufExplorer
### MiniBufExplorer 是什麽？
### MiniBufExplorer 安装
### MiniBufExplorer 使用
### 参考：
- [fholgado/minibufexpl.vim: Elegant buffer explorer - takes very little screen space](https://github.com/fholgado/minibufexpl.vim "")
- [快速浏览和操作Buffer -- 插件: MiniBufExplorer](https://bbs.sjtu.edu.cn/bbsanc,path,%2Fgroups%2FGROUP_3%2FGNULinux%2FSoftware%2FD95E89182%2FD5277E56B%2FA96F89F1C.html "")


---- 

## ***buffer 的使用:***
- 下一个 buffer
`:bn`
- 上一个 buffer
`:bp`
- 打开名称为 filename 的文件
`:e<filename>`
- 显示当前打开的 buffer
`:ls`
- n 为数字，打开第 n 个buffer
`:b<n>`
- 自动补全
`:b<tab>`
- 删除 buffer
`:bd`

----

## 进制操作:
- 正常打开文件，默认添加一个换行行
`vim filename`
- 以二进制打开文件
`vim -b filename`
- 进入 16 进制查看编辑模式,如果在这个模式下执行 `:wq` 命令会把文件直接保存成这个界面(会把当前界面都保存成字符)
`:%xxd`
- 修改 16 进制内容后 回到普通模式，可以看到修改产生的变化，这时执行 `:wq` 不会保存到 16 进制的模式
`:%xxd -r`

```
eg:(Linux 下操作)
echo -n "test" > test.bin
cat test.bin
vim -b test.bin
:%!xxd
vim test.bin
:%!xxd
0x0a
vim -b test.bin
:%!xxd
// 修改 
:%!xxd -r
:wq
```
### 参考:
[在Linux下使用vim配合xxd查看并编辑二进制文件 - killkill - 博客园](http://www.cnblogs.com/killkill/archive/2010/06/23/1763785.html "")
[linux下用vim实现ultraEdit的功能 - Jason Damon - 博客园](http://www.cnblogs.com/Jason-Damon/archive/2013/05/04/3059343.html "")


----
`:q1 ` = `:q!`
----

----
## Vim 帮助文件的跳转

- Jump to a subject: 
Position the cursor on a tag (e.g. |bars|) and hit `CTRL-]`.
- With the mouse: 
 ":set mouse=a" to enable the mouse (in xterm or GUI).  `Double-click` the left mouse button on a tag, e.g. |bars|.
- Jump back:  
Type `CTRL-T` or `CTRL-O` (repeat to go further back).
        
----
## Vim 使用`:find`命令打开文件
使用：
搜索打开文件 filename：
```
:find filename
```
提示：
使用前需要配置`path`变量,添加以下语句到 `.vimrc`文件以可以搜索打开以下文件夹中的文件:
`D:\OneDrive\VIM`
`D:\Proram Files (x86)\hexo\source\_posts`
```
:set path+=.,D:\OneDrive\VIM/*
# 对包含空格文件夹的特殊处理：
:set path+=.,D:\Proram\\\ Files\\\ (x86)\hexo\source\_posts

```
### 参考:
- 《Vim 实用技巧》技巧42 使用`:find`命令打开文件
- [使用vim的find命令快速打开文件 - 王鸿飞的专栏 - 博客频道 - CSDN.NET](http://blog.csdn.net/neosmith/article/details/17308119 "")
- 官方文档 :help path

----

----

## Vim 重复上一个`Ex`命令：
`@：`
### 参考：
- 《Vim 实用技巧》技巧31 重复上次的 Ex 命令

----

## 宏
// Vim 重复上一个宏命令：
`@@`
// 开始录制宏
`q{register}`
// 停止录制宏
`q`
// 查看寄存器中的宏
`:reg a`
### 参考：
- 《Vim 实用技巧》技巧64 宏的读取与执行

----

----
## vim 列模式
`<C-V>`
----
----
## 1. vim 水平滚动

// 设置换行
`set wrap`
// 设置不换行
`set nowrap`
### 在不换行的设置下,普通模式有如下命令:
// 视图向右移动 count 个字符
`[count]zl`
// 视图向左移动 count 个字符
`[count]zh`
// 视图向右滚动半个屏幕
`zL`
// 视图向右滚动半个屏幕
`zH`
// 视图滚动到最右侧
`zs`
// 视图滚动到最右侧
`ze`

### 参考:
- [vim 水平滚动 - lonewolf的个人空间 - 开源中国社区](http://my.oschina.net/lonewolf/blog/207296 "")
----
模式:
次级主题名称

### vim 百分比跳转
