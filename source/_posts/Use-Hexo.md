---

title: Use Hexo
date: 2016-08-05 18:12:39
tags: [Use,Hexo]

---
# Use Hexo

## 1. hexo 命令
### 常用命令
- hexo d
- hexo g
- hexo clean
- hexo n "tit le"
- hexo s
<!-- more -->
[ 预览地址 ](http://localhost:4000/, "")
- hexo v
```
版本信息:
    hexo: 3.2.2
    hexo-cli: 1.0.2
    os: Windows_NT 10.0.14393 win32 x64
    http_parser: 2.6.0
    node: 5.1.0
    v8: 4.6.85.31
    uv: 1.7.5
    zlib: 1.2.8
    ares: 1.10.1-DEV
    icu: 56.1
    modules: 47
    openssl: 1.0.2d
```
### 组合命令:
- `hexo clean && hexo s`
- `hexo clean && hexo d`
## 2. markdown 常用语法
### 代码块
```
这里是代码块
```
### 图片显示
```
![“图片描述”（可以不写）](“图片地址”)

![0808](http://obkpw0khh.bkt.clouddn.com/2016-08-08.png)
```

## 3. Hexo 中 tag，categories 的使用
### hexo 对一篇文章添加多个标签
`tags: [aaa, bbb]`

```
tags:
- foo
- bar

```








## 4. 使用主题 `hexo-theme-icarus`
// 安装主题
`git clone https://github.com/ppoffice/hexo-theme-icarus.git themes/icarus`
// _config.yml
`theme: icarus`
// 更新主题

```
$ cd themes/icarus
$ git pull
```
// 安装搜索插件
$ npm install -S hexo-generator-json-content
// 启用搜索 
`insight: true`




## 5. 使用文章摘要

`<!-- more -->`

## 6. categories 界面 404
`hexo new page categories`




## 参考
- [不知道怎么回事，进入主页文章列表显示全部，而不是显示一部分摘要和more · Issue #44 · litten/hexo-theme-yilia](https://github.com/litten/hexo-theme-yilia/issues/44 "")
- [Markdown代码块中的Markdown语法 · Issue #587 · hexojs/hexo](https://github.com/hexojs/hexo/issues/587 "")
- [请问如何对一篇文章增加多个标签，应该使用什么分隔符？ · Issue #351 · hexojs/hexo](https://github.com/hexojs/hexo/issues/351 "")
- [Hexo使用攻略：（四）Hexo的分类和标签设置 | { GoonX }](http://ijiaober.github.io/2014/08/05/hexo/hexo-04/ "")
- [指令 | Hexo](https://hexo.io/zh-cn/docs/commands.html "")
- [Hexo 最常用的几个命令 | MOxFIVE's Blog](http://moxfive.xyz/2015/12/21/common-hexo-commands/ "")
- [Installation · ppoffice/hexo-theme-icarus Wiki](https://github.com/ppoffice/hexo-theme-icarus/wiki/Installation "") 
- [ppoffice/hexo-theme-icarus: The blog theme you may fall in love with, coming to Hexo.](https://github.com/ppoffice/hexo-theme-icarus "") 
- [Icarus](http://blog.zhangruipeng.me/hexo-theme-icarus/ "预览")
- [Icarus - Wikipedia, the free encyclopedia](https://en.wikipedia.org/wiki/Icarus "")
- [伊卡洛斯 - 维基百科，自由的百科全书](https://zh.wikipedia.org/wiki/%E4%BC%8A%E5%8D%A1%E6%B4%9B%E6%96%AF "")
- [Icarus - Google Search](https://www.google.com/search?sclient=psy-ab&newwindow=1&site=&source=hp&btnG=Search&q=Icarus&oq=&gs_l=&pbx=1 "")


