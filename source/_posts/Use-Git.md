---
title: Use Git
date: 2016-08-08 19:45:21
update:
tags: [Use,Git]
---


### 版本控制系统
- `Subversion`
- `CVS`
- `Perforce`
- 
`snapshot`
`Delta Storage systems`

<!-- more -->

### git 命令
// 设置用户名
`git config --global user.name "name name"`
// 设置用户邮箱
`git config --global user.email "test@test.test"`
// 显示 git 的全局设置
`git config --list`
// 设置 别名
`git config --global alias.st status`
// 使 git 忽略空白的变化
`git config --global apply.whitespace nowarn`
// 使 git 输出时加上颜色
`git config --global color.ui true`
// 编辑 git 全局配置文件
`vi C:\Users\Administrator\.gitconfig`
// 初始化一个 git 仓库
`git init`
// 从远程仓库下载一个仓库,并放置到 test 文件夹
`git clone https://****@github.com/****/****.git test`
// 检查 git 仓库的状态
`git status`
// 把 Untracked files(未被追踪的文件)添加到追踪列表
`git add filename`
// 添加所有 Untracked files 
`git add .`
// 互动模式
`git add -i `
// 提交
`git commit`
// 无提交窗口的提交
`git commit -m "message"`
// 强制提交当前目录下的所有内容
`git commit -a `
// 强制提交当前目录下的所有内容,并直接添加提交信息
`git commit -am "message"`
// 显示变更记录
`git commit -v `
// 查看 commit 记录
`git log`
// 查看 commit 记录详细信息
`git log --stat`
// 查看 commit 记录更详细信息
`git log -p`
// 查看 对象
`git cat-file -p ******(个数?)`
// 查看仓库里**未暂存内容**和**已提交内容**的差异
`git diff`
// 查看暂存区(staging area)里的内容
`git ls-files --stage`
// 把文件从暂存区移除
`git rm-cached filename`
// 把修改撤销
`git checkout -- filename`
// 查看当前的提交(HEAD)所包含的 blob 对象
`git cat-file -p HEAD | head -n 1 | cut -b6-15 | xargs git cat-file -p`
// 查看之前的的提交(HEAD^)所包含的 blob 对象
`git cat-file -p HEAD^ | head -n 1 | cut -b6-15 | xargs git cat-file -p`

// 把一个存在的仓库推送到 github
`git remote add origin https://github.com/****/****.git`
`git push -u origin master`

`fatal: remote origin already exists.`

`git remote rm origin`
`git remote add origin git@github.com:sqsgalaxys/Test-git.git`


[terminal - Github "fatal: remote origin already exists" - Stack Overflow](http://stackoverflow.com/questions/10904339/github-fatal-remote-origin-already-exists "")


// 编辑 git 忽略列表
`vi .gitignore`

### git 目录结构

// 旧版使用的文件夹,新版git一般不会出现
`branches\`

// 下面这个目录灰常重要,里面存储 git 的数据对象
    提交(commits)
    树对象(trees)
    二进制对象(blobs)
    标签对象(tags)
`objects\`

// 各个 refs 的历史信息
`logs\`

// 里面有一个 exclude 文件,指定本项目要忽略的文件
`info\`

// 默认的 "hooks" 脚本文件
`hooks\`

// 表示这你的每个分支指向哪个提交 (commit)
`refs\`

// 保存着上一次提交时的注释信息
`COMMIT_EDITMSG`

// 索引文件,git add 后把要添加的项暂存到这里
`index`

// 项目的配置信息
`config`

// 项目当前在哪个分支的信息
`HEAD`

// 项目的描述信息
`description`
## 传输协议
`git://`
`http://`
`https://`

`ssh,ftp(s),rsync 等协议`
### 目录
工作目录
### 一个 git 项目中文件的状态
1. 未被跟踪的文件(untracked file)
2. 已被跟踪的文件(tracked file)
    a. 被修改但未被暂存的文件(changed but not updated或 modified)
    b. 已暂存可以被提交的文件(changes to be committed或 staged)
    c. 自上次提交以来,未被修改的文件(clean 或 unmodified)
`跟踪 tracked`
`修改 modified`
`暂存 staged`
`提交 committed`


参考:
- [Git 教學(1) : Git 的基本使用 - 好麻煩部落格](http://gogojimmy.net/2012/01/17/how-to-use-git-1-git-basic/ "")
- [Git历险记（一）](http://www.infoq.com/cn/news/2011/01/git-adventures-1 "")
- [Git历险记（二）——Git的安装和配置](http://www.infoq.com/cn/news/2011/01/git-adventures-install-config "")
- [Git 历险记（三）——创建一个自己的本地仓库](http://www.infoq.com/cn/news/2011/02/git-adventures-local-repository "") 
- [Git历险记（四）——索引与提交的幕后故事](http://www.infoq.com/cn/news/2011/03/git-adventures-index-commit "")
- [Git历险记（五）——Git里的分支＆合并](http://www.infoq.com/cn/news/2011/03/git-adventures-branch-merge "")
- 
- 
- 


进阶:
## git 配置
- [Git Book 中文版 - 定制Git](http://gitbook.liuhui998.com/5_7.html "")
- [git-config(1)](https://www.kernel.org/pub/software/scm/git/docs/git-config.html "")
- [Git-Smart-HTTP-Transport(git 对`http(s)`传输协议的优化)](https://git-scm.com/2010/03/04/smart-http.html "smart-http")
- 









# 使用 Git
## 强制从远程仓库获取代码覆盖本地

## 强制用本地代码覆盖远程仓库

## 一些常用的操作
`revert`
`Untracked files`
`vi C:\Users\Administrator\.githubcred`
`SHA 签名串值`
`HEAD 当前提交`
`HEAD^ 前一次提交`
