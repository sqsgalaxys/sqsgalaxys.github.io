---
title: 翻译:-How-to-modify-scripts-behavior-on-signals-using-bash-traps
date: 2018-03-18 21:13:15
tags:
---

# 

/Users/sqsgalaxys/Downloads/sqsgalaxys.github.io/source/_posts/How-to-modify-scripts-behavior-on-signals-using-bash-traps.md
原文:
[How to modify scripts behavior on signals using bash traps - LinuxConfig.org](https://linuxconfig.org/how-to-modify-scripts-behavior-on-signals-using-bash-traps '0.0')



# 目的
这篇教程在于描述如何使用bash shell 内建的 trap命令来使我们的脚本在它接收到一个信号或在其他特定的情形时有特定的操作
# 要求
无特殊要求
# 难度
容易
# 约定 
# - 代表给出的命令应该以 root 权限执行（直接以 root 用户来执行或使用 sudo 命令执行）
$ - 代表给出的命令应该以普通权限的用户执行
# 介绍
当我们写一个重要的脚本,通过使它们可以响应系统的某些信号执行特定的操作,提高它们的鲁棒性是非常重要的.
我们可以通过 bash shell 内建的 trap 达到这一目的.

# 什么是 traps？ 
trap 是一个 bash 机制 它可以自定义脚本的接收到信号时的操作.  这在保证系统在执行脚本出错后恢复系统是非常重要的.  比如写一个脚本,它会在运行时创建一些目录,当它在运行时接收到了 SIGINT 信号,这个脚本会被中断,它创建的目录会被留下来, 我没可以使用traps命令来做一些清除目录的操作.

# Trap 语法
Trap 语法非常简单和易懂：
调用内建的 trap 命令 紧接着在接受到特定信号时需要被执行的命令并指定我们要处理的信号
`trap [-lp] [[arg] sigspec]`
让我们看看 trap 选项的作用
当使用 -l 的选项，trap 命令仅仅显示信号及其对应的数字， 同样的输出你可以通过运行 kill -l 命令来获取 
```
$ trap -l
1) SIGHUP	 2) SIGINT	 3) SIGQUIT	 4) SIGILL	 5) SIGTRAP
6) SIGABRT	 7) SIGBUS	 8) SIGFPE	 9) SIGKILL	10) SIGUSR1
11) SIGSEGV	12) SIGUSR2	13) SIGPIPE	14) SIGALRM	15) SIGTERM
16) SIGSTKFLT	17) SIGCHLD	18) SIGCONT	19) SIGSTOP	20) SIGTSTP
21) SIGTTIN	22) SIGTTOU	23) SIGURG	24) SIGXCPU	25) SIGXFSZ
26) SIGVTALRM	27) SIGPROF	28) SIGWINCH	29) SIGIO	30) SIGPWR
31) SIGSYS	34) SIGRTMIN	35) SIGRTMIN+1	36) SIGRTMIN+2	37) SIGRTMIN+3
38) SIGRTMIN+4	39) SIGRTMIN+5	40) SIGRTMIN+6	41) SIGRTMIN+7	42) SIGRTMIN+8
43) SIGRTMIN+9	44) SIGRTMIN+10	45) SIGRTMIN+11	46) SIGRTMIN+12	47) SIGRTMIN+13
48) SIGRTMIN+14	49) SIGRTMIN+15	50) SIGRTMAX-14	51) SIGRTMAX-13	52) SIGRTMAX-12
53) SIGRTMAX-11	54) SIGRTMAX-10	55) SIGRTMAX-9	56) SIGRTMAX-8	57) SIGRTMAX-7
58) SIGRTMAX-6	59) SIGRTMAX-5	60) SIGRTMAX-4	61) SIGRTMAX-3	62) SIGRTMAX-2
63) SIGRTMAX-1	64) SIGRTMAX

```

非常重要的是 trap 命令只能重新定义可以被脚本响应的信号,像 SIGKILL 和 SIGSTOP 信号不能被捕获,屏蔽或忽略.

除了信号，traps 也可以重新定义一些 伪信号，比如 EXIT, ERR(错误) or DEBUG,在以后后面会深入这些细节
现在我们只要记住，信号可以通过它的名字或它他的数字 甚至可以没有 SIG 前缀,来指定

trap 的 -p 选项,-p 选项的前面不能有命令,否则会报错,
-p 选项会列出已经设置 trap 的信号和对应的列表.
如果指定信号的名字或数字被指定这会列出对应信号对应被设置的 trap 规则,不指定信号的名称或数字的则会显示所有被设置 trap 的信号

` $ trap 'echo "SIGINT caught!"' SIGINT `

我们设置了一个 trap 来捕获 SIGINT 信号，它仅仅是展示 "SIGINT caught" 信息在屏幕上当指定的信号被 shell 接收到
如果我们使用trap 的 -p 选项，这会展示我们刚刚定义的 trap

```
$ trap -p
trap -- 'echo "SIGINT caught!"' SIGINT
```
顺便说一句，这个 trap 现在是 激活的，所以如果我们发送一个 SIGINT 信号，或者使用 kill 命令，或者使用 CTRL-c 快捷键，trap 中绑定的命令将会被执行
（只是打印出 ^C 是因为快捷键绑定（combination)

```
^C
SIGINT caught!
```

# Trap 实战

我们现在来写一个简单的脚本,下面就是

```
#!/usr/bin/env bash
#
# A simple script to demonstrate how trap works
#
set -e
set -u
set -o pipefail

trap 'echo "signal caught, cleaning..."; rm -i linux_tarball.tar.xz' SIGINT SIGTERM 

echo "Downloading tarball..."
wget -O linux_tarball.tar.xz https://cdn.kernel.org/pub/linux/kernel/v4.x/linux-4.13.5.tar.xz &> /dev/null

```
上面的脚本只是试图下载最新的 linux kernel tarball 到启动 wget 的目录 在执行这任务时如果接收到了 SIGINT 或 SIGTERM 信号 (注意你如何在一行中指定不止一个信号) 下载的部分文件会被删除

In this case the command are actually two: the first is the echo which prints the message onscreen, and the second is the actual rm command (we provided the -i option to it, so it will ask user confirmation before removing), and they are separated by a semicolon. Instead of specifying commands this way, you can also call functions: this would give you more re-usability. Notice that if you don't provide any command the signal(s) will just be ignored! 
在这个例子中，命令实际是两个，第一个是 echo 第二个是实际执行 rm 命令,我们提供 -i 选项给他， 所以它会在删除前要求用户确认 而且他们以逗号分割，除了这样指定命令以外，你也可以调用函数,这样可以给你高可用性 注意，如果你不提供任何命令，信号会被忽略 

这是在接收到 SIGINT 信号时，脚本的输出:

```
$ ./fetchlinux.sh
Downloading tarball...
^Csignal caught, cleaning...
rm: remove regular file 'linux_tarball.tar.xz'?

```
记住一个非常重要的点: 像上面这样当一个脚本通过信号终止， 他的退出码将是 128 与信号数字的和， 你可以看到，

```
$ echo $?
130

```
最后,你可以停用 trap:调用 trap 紧跟着 sign 跟着 信号的名字或者数字

` trap - SIGINT SIGTERM `
这个信号将会恢复原来的作用 
# 伪信号
就像上面提到的 trap 不仅可以被用来让脚本响应信号,也可以响应被称作假冒信号的信号 它们不是典型的信号,但是一致的确定的情形也可以被指定 trap

## EXIT
当 EXIT 被指定在 trap 中,被 trap 命令参数将会在退出 shell 时执行
## ERR (错误)
当一个命令返回一个非零的退出值, 附带一些异常时 trap 的参数被执行.它和 shell errexit 选项类似 这个命令必须不是一个 while 或 until 循环的一部分, 它必须不是 if 条件的一部分,也不能是 && 或 || 条件的一部分 并且它的值不能通过 ! 反转

## DEBUG
This will cause the argument of the trap to be executed before every simple command, for, case or select commands, and before the first command in shell functions
trap 的命令参数将会在一些非常简单的命令 `for` `case` 或者 `select` 命令后,并且在 shell 函数的第一个命令之前执行

RETURN
返回
The argument of the trap is executed after a function or a script sourced by using source or the . command.
trap 的命令参数将会在以下情形执行:
- 执行完一个函数
- 一个脚本被 source命令加载
- `.` 命令


