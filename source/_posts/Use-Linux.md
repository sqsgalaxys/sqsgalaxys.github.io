---
title: Use Linux
date: 2016-08-08 09:49:17
update:
tags: [Use,Linux]
---

---
Linux 启动设置:

`sudo vi /etc/inittab`
<!-- more -->

```
# Default runlevel. The runlevels used are:
#   0 - halt (Do NOT set initdefault to this)
#   1 - Single user mode
#   2 - Multiuser, without NFS (The same as 3, if you do not have networking)
#   3 - Full multiuser mode
#   4 - unused
#   5 - X11
#   6 - reboot (Do NOT set initdefault to this)
#

#id:3:initdefault:
#id:5:initdefault:
```
[Linux启动界面切换:图形界面-字符界面(转) - 草原和大树 - 博客园](http://www.cnblogs.com/JemBai/archive/2011/09/15/2177386.html "")
---

重启命令
`sudo reboot`
关机
`sudo poweroff`
[command line - How do I shut down or reboot from a terminal? - Ask Ubuntu](http://askubuntu.com/questions/187071/how-do-i-shut-down-or-reboot-from-a-terminal "")

---

---

---

`echo` 命令
echo -n

---

---

`od` 命令

---

---

`chkconfig` 命令
'chkconfig --list'

---

----
## 安装配置 ftp 

下载安装
`yum -y install vsftpd`
`chkconfig --level 2345 vsftpd on`
`touch /var/log/vsftpd.log`
`vi /etc/vsftpd/vsftpd.conf`
```
`local_enable=YES`
`anonymous_enable=NO`
```
`adduser -d / -g ftp -s /sbin/nologin sqsgalaxys`
`passwd sqsgalaxys`

配置
    服务配置
    用户配置
启动

## 安装配置 ftp 
// 安装 vsftpd
`yum -y install vsftpd`
// 创建日志文件
`touch /var/log/vsftpd.log`
// 查看 vsftpd 服务启动情况

`chkconfig --list`

```

[root@localhost]~# chkconfig --list|grep ftp
vsftpd         	0:off	1:off	2:off	3:off	4:off	5:off	6:off
[root@localhost]~# 

```

// 配置服务器开机自动启动 ftp 服务
`chkconfig --level 2345 vsftpd on`
// 启动 ftp 服务
`service vsftpd start`
// 查看 ftp 服务状态
`service vsftpd status`
// 重启 ftp 服务
`service vsftpd restart`
// 关闭 ftp 服务
`service vsftpd stop`
// 编辑 vsftpd 配置文件
`vi /etc/vsftpd/vsftpd.conf`
// 不允许匿名访问
`anonymous_enable=NO`
// 设定可以本地用户访问 ?虚拟宿主用户,虚拟用户
`local_enable=YES`
// 使用户不能离开主目录 配合`/etc/vsftpd/chroot_list`使用
`chroot_list_enable=YES`
// 设定 vsftpd 的服务日志保存路径
`xferlog_file=/var/log/vsftpd.log`
// 允许使用 ASCII 模式上传
`ascii_upload_enable=YES`
// 设定支持 ASCII 模式的上传和下载功能
`ascii_download_enable=YES`
// PAM 认证文件名 PAM 根据`/etc/pam.d/vsftpd`进行认证
`pam_service_name=vsftpd`

// 添加用户 
adduser -d / -g ftp -s /sbin/nologin sqsgalaxys
// 设置密码
passwd sqsgalaxys
// 权限设置?
chown -R sqsgalaxys:ftp/tmp/sqsgalaxys

㕜
// 查看进程?
ps -ef | grep ftp
chkconfig --list
chkconfig --list|grep ftp
yum -y install vsftpd
chkconfig --level 2345 vsftpd on
chkconfig --list|grep ftp
chkconfig --list|grep tomcat
service vsftpd status
vi /etc/vsftpd/vsftpd.conf
adduser -d / -g ftp -s /sbin/nologin sqsgalaxys
adduser -d /tmp -g ftp -s /sbin/nologin sqsgalaxys
passwd sqsgalaxys
chown -R sqsgalaxys:ftp/
chown -R sqsgalaxys:ftp/tmp
chown -R sqsgalaxys:ftp/tmp/sqsgalaxys
service vsftpd restart
vi /etc/vsftpd/vsftpd.conf
service vsftpd restart


Note:
`chroot`:限制所列的ftp用户只能访问其被指定的`Home`目录
参考:
- [（一）Linux环境部署(Centos+Nginx+Tomcat+Mysql)-FTP安装_Linux教程 | 帮客之家](http://www.bkjia.com/Linuxjc/1009970.html "")
- [vsftpd - Secure, fast FTP server for UNIX-like systems](https://security.appspot.com/vsftpd.html "")

