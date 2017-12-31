---

title: Use nmap
date: 2016-08-15 09:11:55
update:
tags: [Use,Nmap]

---
# Nmap
## Host discovery
PS n - tcp syn ping 
PA n - tcp ack ping
PU n - udp ping
PM - nctmask req
PP - timestamp rcq
PE - echo req
sL - list scan
PO - protocol ping
PN - no ping
n - no DNS
R - DNS resolution for all targets

## Port scanning techniques
sS
sT
sU
sA
sW
sY
sZ
sO
sN sF sX - null,fin,xmas








软件安装环境是win7、使用Zenmap， nmap6.49BETA2

扫描主机端口
nmap -T4 -A -v 192.168.0.207



nmap -O –osscan-guess 192.168.0.207
版本扫描（要在扫描端口后）
nmap -sV 192.168.0.207
Idle scan 使用另一个目标网张的主机发送数据包
nmap -sL 192.168.0.23 192.168.0.207

其它选项说明：
-A 操作系统检测
-6 ipv6检测
-T 时间模板，0-5
-v 增加冗余
-exclude 排除扫描地址
-exclude file 排除文件里的ip地址

### 根据网段扫描获取主机列表
// 普通扫描
`nmap -sn 192.168.1.*`
// ARP Ping 扫描:
`nmap -PR 192.168.1.*`
### 针对主机扫描端口
SYN半开扫描
`nmap -sS 192.168.1.1`
TCP扫描
`nmap -sT 192.168.1.1`
ftp弹跳扫描
`nmap -b username:password@server:port`

nmap -sV 192.168.1.88
nmap -O 192.168.1.88

设置Nmap扫描的端口范围

其它常用选项
-A 同时开启系统探测与服务版本探测(也称激烈模式).
-v 开启冗余模式,这样能得到详细的信息报告.
-e <interface> 使用指定网卡发送数据报文.
-6 启用ipv6扫描




## Nmap Target Selection

// Scan a single IP
`nmap 192.168.1.1`


// Scan a host	
`nmap www.testhostname.com`

// Scan a range of IPs	
nmap 192.168.1.1-20

// Scan a subnet	
`nmap 192.168.1.0/24`

// Scan targets from a text file	
`nmap -iL list-of-ips.txt`

Nmap Port Selection
Scan a single Port	nmap -p 22 192.168.1.1
Scan a range of ports	nmap -p 1-100 192.168.1.1
Scan 100 most common ports (Fast)	nmap -F 192.168.1.1
Scan all 65535 ports	nmap -p- 192.168.1.1
Nmap Port Scan types

Scan using TCP connect	nmap -sT 192.168.1.1
Scan using TCP SYN scan (default)	nmap -sS 192.168.1.1
Scan UDP ports	nmap -sU -p 123,161,162 192.168.1.1
Scan selected ports - ignore discovery	nmap -Pn -F 192.168.1.1
Service and OS Detection

Detect OS and Services	nmap -A 192.168.1.1
Standard service detection	nmap -sV 192.168.1.1
More aggressive Service Detection	nmap -sV --version-intensity 5 192.168.1.1
Lighter banner grabbing detection	nmap -sV --version-intensity 0 192.168.1.1

Nmap Output Formats

Save default output to file	nmap -oN outputfile.txt 192.168.1.1
Save results as XML	nmap -oX outputfile.xml 192.168.1.1
Save results in a format for grep	nmap -oG outputfile.txt 192.168.1.1
Save in all formats	nmap -oA outputfile 192.168.1.1

Digging deeper with NSE Scripts

Scan using default safe scripts	nmap -sV -sC 192.168.1.1
Get help for a script	nmap --script-help=ssl-heartbleed
Scan using a specific NSE script	nmap -sV -p 443 –script=ssl-heartbleed.nse 192.168.1.1
Scan with a set of scripts	nmap -sV --script=smb* 192.168.1.1

A scan to search for DDOS reflection UDP services

Scan for UDP DDOS reflectors	nmap –sU –A –PN –n –pU:19,53,123,161 –script=ntp-monlist,dns-recursion,snmp-sysdescr 192.168.1.0/24
HTTP Service Information

Gather page titles from HTTP services	nmap --script=http-title 192.168.1.0/24
Get HTTP headers of web services	nmap --script=http-headers 192.168.1.0/24
Find web apps from known paths	nmap --script=http-enum 192.168.1.0/24
Detect Heartbleed SSL Vulnerability

Heartbleed Testing	nmap -sV -p 443 --script=ssl-heartbleed 192.168.1.0/24
IP Address information

Find Information about IP address	nmap --script=asn-query,whois,ip-geolocation-maxmind 192.168.1.0/24




### 参考:
- [Nmap: the Network Mapper - Free Security Scanner](https://nmap.org/ "官网")
- [Nmap - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Nmap "")
- [Nmap - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/Nmap#Nmap.E5.9F.BA.E6.9C.AC.E5.91.BD.E4.BB.A4.E5.92.8C.E5.85.B8.E5.9E.8B.E7.94.A8.E6.B3.95 "")
- [Nmap Cheat Sheet | HackerTarget.com](https://hackertarget.com/nmap-cheatsheet-a-quick-reference-guide/ "")
- [Nmap 介绍与基本使用教程](http://blog.sbw.so/Article/index/Nmap 介绍与基本使用教程/Nmap%20%E4%BB%8B%E7%BB%8D%E4%B8%8E%E5%9F%BA%E6%9C%AC%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B.html "")

