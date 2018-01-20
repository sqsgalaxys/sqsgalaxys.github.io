---

title: 记录 Linux 磁盘空间被占满的解决过程  
date: 2018-01-20 07:24:11  
tags:  

---

# 记录 Linux 磁盘空间被占满的解决过程
## 查看磁盘占用情况
``` bash
-----------» df -lh
Filesystem      Size  Used Avail Use% Mounted on
/dev/vda1        30G   30G   20K 100% /
devtmpfs        911M     0  911M   0% /dev
tmpfs           920M   16K  920M   1% /dev/shm
tmpfs           920M   89M  831M  10% /run
tmpfs           920M     0  920M   0% /sys/fs/cgroup
tmpfs           184M     0  184M   0% /run/user/0
```
## 不断查看 / 下面目录文件(夹)大小找到大文件(夹)
``` bash
-----------» cd / && du -sh *
0	bin
148M	boot
16K	dev
178M	etc
1.3G	home
0	lib
0	lib64
0	media
4.0K	meta.js
0	mnt
3.9G	opt
du: cannot access ‘proc/5030/task/5030/fd/4’: No such file or directory
du: cannot access ‘proc/5030/task/5030/fdinfo/4’: No such file or directory
du: cannot access ‘proc/5030/fd/4’: No such file or directory
du: cannot access ‘proc/5030/fdinfo/4’: No such file or directory
0	proc
1.6G	root
89M	run
0	sbin
0	srv
0	sys
12K	tmp
68K	Users
3.7G	usr
20G	var
-----------» cd /var && !!
-----------» cd /var && du -sh *
0	adm
107M	cache
0	crash
220K	db
0	empty
0	games
0	gopher
0	kerberos
2.2G	lib
0	local
0	lock
                                    17G	log
0	mail
0	nis
16K	opengrok
0	opt
0	preserve
0	run
132K	spool
4.0K	tmp
....
```
可以看到 log 文件夹有 17 GB 大小,进入log目录查看目录下文件大小:

``` bash
-----------» ^var^var/log
-----------» cd /var/log && du -sh *
0	agent_debug_info_msgs.log
1.8M	AgentMonitor.log
11M	AgentMonitor.log.1
11M	AgentMonitor.log.2
11M	AgentMonitor.log.3
11M	AgentMonitor.log.4
11M	AgentMonitor.log.5
3.6M	ambari-server
1.2M	anaconda
34M	audit
0	auth.log
0	boot.log
0	boot.log-20180111
12K	boot.log-20180112
0	boot.log-20180115
0	boot.log-20180116
0	boot.log-20180117
0	boot.log-20180119
0	boot.log-20180120
4.8M	btmp
10M	btmp-20180101
5.9M	CloudAgent.log
11M	CloudAgent.log.1
11M	CloudAgent.log.10
11M	CloudAgent.log.2
11M	CloudAgent.log.3
11M	CloudAgent.log.4
11M	CloudAgent.log.5
11M	CloudAgent.log.6
11M	CloudAgent.log.7
11M	CloudAgent.log.8
11M	CloudAgent.log.9
0	CloudUpdate_debug_info_msgs.log
1.4M	CloudUpdate.log
24K	cron
44K	cron-20171224
52K	cron-20171231
52K	cron-20180107
40K	cron-20180115
1.7M	denyhosts
32K	dmesg
0	dmesg.0
32K	dmesg.old
0	dpkg.log
4.0K	grubby
4.0K	grubby_prune_debug
488K	httpd




                17G	jenkins




24K	lastlog
0	maillog
0	maillog-20171224
0	maillog-20171231
0	maillog-20180107
0	maillog-20180115
1.1M	messages
27M	messages-20171224
31M	messages-20171231
28M	messages-20180107
18M	messages-20180115
184K	mongodb
92K	mysqld.log
84K	nginx
0	ntp
24K	ntp.log
0	ntpstats
0	ppp
4.0K	privoxy
0	qemu-ga
544K	secure
860K	secure-20171224
36K	secure-20171231
820K	secure-20180107
564K	secure-20180115
880K	secure.bak
2.1M	shadowsocksr.log
0	spooler
0	spooler-20171224
0	spooler-20171231
0	spooler-20180107
0	spooler-20180115
0	tallylog
48K	tuned
4.0K	udinstall.log
0	wpa_supplicant.log
308K	wtmp
4.0K	yum.log
36K	yum.log-20180101
```
## 删除大文件(夹)

jenkins 的日志有 17GB,赶紧停止 jenkins:

``` bash
-----------» service jenkins stop   
Stopping jenkins (via systemctl):                          [  OK  ]
-----------»
```
删除 jenkins 日志:
``` bash
rm -rf /var/log/jenkins
```
## 命令总结:
```
# 查看磁盘使用情况
df -lh
# 查看当前文件夹下面文件(夹)的大小
du -sh *
```

## 学习到的经验:
在装完一个应用后需要观察应用一段时间,看看系统的运行是否正常.
