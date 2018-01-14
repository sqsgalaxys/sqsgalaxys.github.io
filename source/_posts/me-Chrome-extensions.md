---

title: me Chrome extensions
date: 2018-01-14 23:34:58
tags:

---

# 我的 Chrome 插件

插件本地存放目录:
`~/Library/Application Support/Google/Chrome/Default/Extensions`
插件地址:

``` python
# -*- coding: utf-8 -*-
import socket
import socks
import requests
from bs4 import BeautifulSoup
import time

SOCKS5_PROXY_HOST = '127.0.0.1'
SOCKS5_PROXY_PORT = 1086  # socks 代理本地端口
default_socket = socket.socket
socks.set_default_proxy(socks.SOCKS5, SOCKS5_PROXY_HOST, SOCKS5_PROXY_PORT)
socket.socket = socks.socksocket

# url = 'https://chrome.google.com/webstore/detail/infolite/ipjbadabbpedegielkhgpiekdlmfpgal'
baseUrl = 'https://chrome.google.com/webstore/detail/'

extensions = [
    'aabcgdmkeabbnleenpncegpcngjpnjkc',
    'aajodjghehmlpahhboidcpfjcncmcklf',
    'aalnjolghjkkogicompabhhbbkljnlka'
]

for extension in extensions:
    url = baseUrl + extension
    html_source = requests.get(url, headers={
        "User-Agent": "Mozilla/5.001 (windows; U; NT4.0; en-US; rv:1.0) Gecko/25250101"}).text
    if html_source:
        try:
            # 正常的操作
            print('ok')
            soup = BeautifulSoup(html_source, 'html.parser')
            # <h1 class="e-f-w">OneTab</h1>
            # 插件的标题
            # print("标题: " + soup.html.find_all("title")[0].text)
            # 合成 markdown 链接
            title = soup.html.find_all("title")[0].text
            print('### [' + title + ']' + '(' + url + " '0.0'" + ')')
            # <pre class="C-b-p-j-Oa">
            # 插件的自我介绍
            print("介绍: " + soup.find_all("pre", class_="C-b-p-j-Oa")[0].text)
            print("-------------")
        except:
            # 发生异常，执行这块代码
            print('fail for: ' + '[' + url + ']')
        else:
            print('ok')
            # 如果没有异常执行这块代码

    else:
        print('fail for: ' + '[' + url + ']')
    # Wait for 5 seconds
    time.sleep(4)


```



## 介绍方式:
- 插件下载地址:
- 插件自己的介绍:
- 我的介绍(TODO):

### [Easy Auto Refresh - Chrome Web Store](https://chrome.google.com/webstore/detail/aabcgdmkeabbnleenpncegpcngjpnjkc '0.0')
> Automatically reloads web pages after any number of seconds.
> 
> Features:
> * Refresh pages after a set number of seconds.
> * Set different delays per page or tab.
> * Remembers your settings per page.
> * Remembers web page scroll position.
> 
> Simply enter the number of seconds between reloads and click Start. You can specify different settings per tab. Preferences are saved per web page URL. The countdown pauses while typing. To stop refreshing of the tab, just click Stop.
> 
> Register your copy of Easy Auto Refresh to unlock advanced options, including:
> 
> * Save preferences per web page URL or per web site domain.
> * Enable random countdown intervals.
> * Choose specific times of day.
> * Reload all tabs in the window.
> * Automatically click a button, link, or element on the page.
> * Navigate to a url from a list at each countdown interval.
> * Show a notification and play a sound when text is found in the page.
> * Display the last and next refresh time.
> * Clear cache.
> * Receive access to future enhancements.
> 
> Privacy Policy and Terms of Service
> 
> By installing this add-on, you agree to the following privacy policy http://dummysoftware.com/chrome-privacy.html

### [NooBoss - Chrome Web Store](https://chrome.google.com/webstore/detail/aajodjghehmlpahhboidcpfjcncmcklf '0.0')

> 介绍: Take the full control of your Chrome apps/extensions by using NooBoss!
> With NooBoss, you can check the details of your Chrome apps/extensions, from permissions they need to the date they got updated. You can also check the community tags for each apps/extensions, and tag it so others will know if it's a good app/extension or not. You can also set rules for extensions so that they will be enabled only when you opened certain websites.
> 
> Functions that NooBoss provides:
> *Manage your apps
> ---enable/disable/remove one or a bunch of apps
> *NooBoss community
> ---get apps recommended by NooBoss community for the website you are visiting
> ---you can recommend useful apps to NooBoss community
> ---you can tag useful or spammy apps
> *Auto state management
> ---automatically enable/disable apps base on auto state rules
> ---(you can save memory)
> ---(enable apps only when you need them)
> *Show history of apps
> ---installation, removal, enabling, disabling
> ---show the version change
> ---(you can tell when did apps got updated)
> *Show detailed information of apps
> ---download crx file
> ---open manifest file
> ---see permissions
> ---And a lot more informations
> 
> You can find recent changes on https://github.com/AInoob/NooBoss/commits/master

### [Context - Chrome Web Store](https://chrome.google.com/webstore/detail/aalnjolghjkkogicompabhhbbkljnlka '0.0')
> 介绍: Take a look at your extensions, do you really use all of them all the time? Rather not. Do you know that these unused extensions are taking resources and space from you? They may also bug you with distracting icon animations and notifications. With Context you can stop that. Simply put extensions that you use for work, fun, shopping, socializing etc. into different groups ("contexts") and with one click switch between them.
> 
> Extra:
> - mix contexts with each other using +/- buttons
> - configuration import / export / synchronisation
> - first run step by step tutorial
> - when new extension is installed Context will let you assign it to appropriate groups via notification window - no need to open configuration page

### [Restlet Client - REST API Testing - Chrome Web Store](https://chrome.google.com/webstore/detail/aejoelaoggembcahagimdiliamlcdmfm '0.0')
> 介绍: [Please scroll down for permissions explanation]
> 
> Restlet Client is designed and developed by developers for developers to make direct HTTP / REST resource discovery, testing and test automation easier. Restlet Client’s main functions include: 
> 
> 1. API Invocation and Interaction
> Through an intuitive browser interface, make calls to HTTP APIs to validate their functional behavior, testing different parameters and values without writing a program or script.
> 
> You can easily import your Postman Collections, Swagger / OAS and HAR.
> 
> 2. API Testing
> Create and run unit tests as well as complex API scenarios decorated by assertions to validate your APIs.
> 
> 3. API Automation
> API scenarios and tests execution can be easily done with Maven plugin which you can integrate to your CI/CD. (e.g. Jenkins, Travis CI, Bamboo...)
> 
> Key features:
>   - Call web APIs through a visual tool
>   - Save calls history, locally or to the cloud, and organize it in projects
>   - Build dynamic requests with custom variables, security and authentication 
>   - Analyze and validate responses, compare them to history
>   - Combine multiple API requests into API scenarios with variables
>   - Share work with colleagues
>   - Integrate API testing to CI/CD toolchain through plugins for Maven, Jenkins, Travis CI, CircleCI...
> 
> 4. API Orchestration
> With Restlet Client, you can combine multiple API requests into API scenarios. Variables can be passed from one response to the next request, creating realistic scenarios that closely emulate real-life use of the API by a frontend or mobile application
> 
> 
> Restlet Client is part of the Restlet platform: the API First Platform with a comprehensive and integrated set of capabilities for API developers.
> 
> 
> Why Restlet Client requires "Read and change all your data on the websites you visit" and "Communicate with cooperating websites" permissions?
> 
> Chrome applications which need access to internet resources must declare it in their manifest. It can be a list of URLs or URL mask; e.g. http://*/* allowing access to any URL. 
> 
> Allowing access to any URL is a primary function of Restlet Client, and the URL mask with wildcards is in interpreted by Chrome Store as:
> 
> This app can access:
> Read and change all your data on the websites you visit
> 
> Which is true, but doesn't mean that the app is doing something bad. Restlet Client doesn't collect your data.
> 
> For news and updates, follow Restlet on Twitter: @Restlet

### [Free Download Manager Chrome extension - Chrome Web Store](https://chrome.google.com/webstore/detail/ahmpjcflkgiildlgicmcieglgoilbfdp '0.0')
> 介绍: The sole purpose of this extension is integration with Free Download Manager. FDM is a fast and reliable download manager and accelerator that improves your experience with downloads and helps you organize them in an easy manner.
> If you want to help us make Free Download Manager (or this Chrome extension) better - you are always welcome on our forum where you can post bug reports, feature suggestions, and ideas, as well as get support for any issues you stumbled upon with FDM: http://www.freedownloadmanager.org/board/
> 
> Note: Windows or Mac only! Requires FDM to be installed to work properly.

### [扇贝助手增强版 - Chrome Web Store](https://chrome.google.com/webstore/detail/aibonellgbdkldghjgbnapgjblebfkbl '0.0')
> 介绍: 更多安装及使用说明，请 访问 
> 
> http://josephjctang.com/shanbay-crx/ 
> 
> 反馈问题，请到：
> 
> https://github.com/jinntrance/shanbay-crx/issues
> 
> 2017.7.15 update 1.13.7
> 
> general bug fixes and improvements.
> 
> 2017.5.8 update 1.13.6.5
> 
> general bug fix.
> 
> 2017.2.18 update 1.13.6.2
> 
> linksgo2011 添加单复数、时态、常用短语。
> 
> 2017.1.10 update 1.13.6.1
> 
> wanglongbiao 修复扇贝网修改导致不可用的问题。
> 
> 2016.11.4 update 1.13.6
> 
> 修复popup 定位问题
> 
> 2016.6.5 update 1.13.4
> 
> general bug fix
> 
> 2016.3.27 update 1.13.3
> 
> 修复多数不可用问题
> 
> 2015.12.6 update 1.13.1
> 
> 1. add new webster key
> 
> 2015.10.6 update 1.13.0
> 
> 1. fix bugs.
> 2. add/replace Webster keys.
> 
> 2015.5.6 update 1.12.10
> 1. 更新jquery和howler.js
> 2. 修正https 下发音问题
> 3. 添加跳转到用户分享笔记和创建笔记的快捷键
> 
> 2015.3.2 update 1.12.7 
> 1. 感谢贡献keys的童鞋。
> 2. 删除被webster禁用的keys。
> 3. 修复scrollable的element 解释框位置不对的问题。 
> 
> 2015.1.16 update 1.12.6
> Thanks to Zhiyong Wang for his Webster key.
> 
> 2014.12.23 更新 1.12.5
>  1. 添加“忘词”。
> 
> 2014.12.11 更新 1.12.4
>  1. fix bugs；
>  2. 添加右键“选词查字”是否显示的设置。
> 
> 2014.11.25 更新 1.12.3.3
>  1. 解决“多次提示不登录，登录后会显示非常多的tabs”的bug。
> 
> 2014.10.9 更新 1.12.3.2
>  1. 修正Chrome版本更新後不提醒的bug；
>  2. 修改網頁內嵌入iframe插件劃詞查義不可用的bug。
>  3. shanbay.com更新后修改。
> 
> 2014.6.25 更新 1.12.2
> 
>  1. 添加背单词提醒
>  2. 解决扇贝API更新后的部分bugs
> 
> 2014.3.30 更新1.11.1(Thanks to Arbor Lin)
>  1. 解决乱码问题。
> 
> 2014.2.11 更新1.11
> 
>  1.修正改版后bugs
>  2.添加wanghao贡献的key
> 
> 2013.11.16 更新 1.10
>  1.可自行添加webster key
>  2.修正扇貝改版後的bugs
>  3.感谢@SCIN 贡献key
> 
> 2013.9.17 更新 1.9.2
> 应扇贝要求删除自动添加词根词缀到笔记
> 
> 2013.9.17 更新1.9
> 
> 批量添加生詞，批量添加單詞書。
> 
> 2013.9.5 更新1.8.4.7
> 
> 修正bugs，加快词根、派生加载穩定性和速度。
> 
> 2013.8.31 更新 1.8
> a.添加对已购买词根派生用户的支持，扇贝未提供的词根派生再由该助手查询；
> b.修改部分快捷键，不与扇贝自生快捷键冲突，派生改用X、全屏改用W、词根改用E；
> c.修正划词查义中的bugs
> 
> 查词等修改自https://chrome.google.com/webstore/detail/扇贝助手/nmbcclhheehkbdepblmeclbahadcebhj 多谢。

### [Anki 划词制卡助手 - Chrome Web Store](https://chrome.google.com/webstore/detail/ajencmdaamfnkgilhpgkepfhfgjfplnn '0.0')

> 介绍: 英语学习者在新闻网站或者社交媒体上进行增量阅读(Incremental Reading)或者沉浸式阅读(Immersion Reading)时，往往需要能够随手翻译生词帮助理解，而阅读过后，又希望能将刚才阅读时遇到的生词和上下文语句作为笔记保存，以供日后复习。Anki本身提供了不错的间隔式复习功能，但是制卡的过程略微繁琐。Anki划词制卡助手，就是为了帮助学习者在阅读的同时，将生词，释义，音标，语音音频和上下文例句一键保存并制作成Anki卡片，以供日后复习。
> 使用方法
> 1. 鼠标移到单词，按Shift翻译。
> 2. 按喇叭图标，听取单词发音。
> 3. 按加号按钮，在Anki PC制卡。
> 注意事项：
> PC端制卡需要安装ankiconnect插件。
> 
> 更新日志：
> 0.99.7
> 1. Ankiweb改版，不再支持云端制卡功能。
> 2. 适配Ankiconnect2.0
> (如果后台显示版本不匹配警告，请去anki addon官网或者选项的ankiconnect链接处下载最新版ankiconnet.py文件)  
> 
> 0.99.6
> 1. 因Ankiweb服务条款限制，暂停Ankiweb云端制卡功能。
> 2. 修正因插件造成的某些网站(如：youtube)访问异常。
> 0.99.5
> 1. 再次修正云端制卡问题。
> 0.99.4
> 1. 修正云端制卡问题。
> 2. 修正在线词典部分翻译内容缺失问题。
> 3. 增加单词星级。
> 4. 适配低版本浏览器(XP版Chrome v49)
> 
> 0.99.3
> 1. 修改弹窗代码，支持较低版本Chrome内核浏览器(如极速360)
> 2. 调整弹窗行为
> - 浏览器窗口滚卷时，翻译弹窗不再消失。
> - 翻译弹窗内显示位置重置，不受上次显示内容影响。
> 
> 0.99.1-0.99.2
> 1. 调整在线词典超时和排序。
> 2. 调整一词多义制卡方式。
> 3. 简化弹窗并去除多余要素和样式。
> 
> 0.99
> 1. 增加在线词典选项。
> 
> 0.98.1-0.98.2
> 1. 增加卡片自定义标签(多标签用空格分隔)。
> 2. 增加例句单词填空字段{cloze}。
> 
> 0.98
> 1. 整合Ankiweb制卡。
> 
> 0.97
> 1. 例句中高亮生词。
> 
> 0.96:
> 1. 优化单词原型匹配。
> 
> 0.95:
> 1. 补遗3900+词典词条，修正仅高亮词根的错误
> 2. 词组匹配后优先显示，优化词语搜索性能。
> 
> 0.94: 
> 1. 单词原型查询：使用了全量词性映射表，消除了因单词变形而找不到单词的问题。
> 2. 去掉防重限制: 一次多义的单词可以在Anki反复添加(卡片重复交由anki管理)。
> 3. 弹窗格式改动：具有词性彩色高亮和所查的关键字在例句中高亮功能。
> 4. 匹配词组显示：在词根的单词解释里，会把相关词组高亮。
> 
> 0.93
> 1. first version forked from FooSoft Yomichan Chomre Extension
> 
> 作者主页：
> http://ninja33.github.io
> 

### [豆瓣电影下载神器——豆瓣皮 - Chrome Web Store](https://chrome.google.com/webstore/detail/akaipdifbckmdehebihpbhniokobpfmi '0.0')

> 介绍: 1.在您浏览豆瓣电影页面的时候，自动搜索电影下载资源，并显示下载按钮。
> 2.在任何网页选中关键字，点击鼠标右键搜索电影
> 3.点击插件图标，快速搜索电影
> 
> 资源来自豆瓣皮: http://movie.doubanpi.com
> 
> 关于《豆瓣皮》的介绍:
> 
> 网站主要针对 豆瓣电影 用户。
> 
> 使用举例：当用户访问电影《复仇者联盟》（网址：http://movie.douban.com/subject/1866479/）的时候，可直接在网址中的 douban 和 .com 之间加入 pi 形成http://movie.doubanpi.com/subject/1866479/，然后回车访问，可直接进入到当前电影的下载页面。
> 
> 前后网址对比：
> http://movie.douban.com/subject/1866479/
> http://movie.doubanpi.com/subject/1866479/
> 
> 网站实时全网搜集所有的电影下载资源（电驴、BT、磁力链、快播等）

### [Pomotodo - Chrome Web Store](https://chrome.google.com/webstore/detail/algakdpepofkajponmledaldoloboinf '0.0')
> 介绍: Pomotodo is a simple app based on Pomodoro Technique® and To-do List. With its beautiful and simple design, Pomotodo can help you to collect, process, organize, review and do. Start using Pomotodo today, Do Remarkable Work!

### [网易有道词典鼠标取词插件 - Chrome Web Store](https://chrome.google.com/webstore/detail/aohddidmgooofkgohkbkaohadkolgejj '0.0')
> 介绍: 在安装了网易有道词典客户端的Windows电脑上，安装该插件后能在浏览器中更快更精准得取词。

### [Google Drive - Chrome Web Store](https://chrome.google.com/webstore/detail/apdfllckaahabafndbhieahigkjlhalf '0.0')
> 介绍: With Google Drive, you can now access your files, even the big ones, from wherever you are. Share them with whomever you want, and edit them together in real time.
> 
> **Create and collaborate**
> Google Docs is built right into Google Drive, so you can work together in real time on documents, spreadsheets and presentations. Share your stuff with others, add and reply to comments and even make edits on the go.
> 
> **Store everything safely and access it anywhere**
> You can access your stuff from anywhere—in your home, at the office, while running errands and from all your devices. Install Drive on your Mac or PC, download the mobile app to your phone or tablet, or visit anytime at drive.google.com. 
> 
> **Search everything**
> Search by keyword and filter by file type, owner and more. Drive can even recognize content in your scanned documents and images. 
> 
> We get you started with 15 GB free. Learn more at drive.google.com.

### [Chrome Tips Beta (by Google) - Chrome Web Store](https://chrome.google.com/webstore/detail/bdmbgfhokojnnaliemjgbahnfeggocpe '0.0')
> 介绍: The Chrome Tips extension provides handy tips to help you get the most out of Chrome. The tips range from basics for beginners to advanced features for power users, and we try to show them when they can be most helpful to you. We hope you have fun unlocking Chrome’s great features—happy browsing!
> 
> Note: Chrome Tips is in Beta, and is currently only available in English.

### [Web Developer - Chrome Web Store](https://chrome.google.com/webstore/detail/bfbameneiokkgbdmiekhjnmfkcnldhhm '0.0')
> 介绍: The Web Developer extension adds a toolbar button to the browser with various web developer tools. This is the official port of the Web Developer extension for Firefox.
> 
> 
> The best place for support is not in the reviews section below, but on the Web Developer site in the help:
> 
> http://chrispederick.com/work/web-developer/help/
> 
> Also available there are a full set of release notes:
> 
> http://chrispederick.com/work/web-developer/history/chrome/

### [搜索拐杖 - Chrome Web Store](https://chrome.google.com/webstore/detail/bgenmocoeejdpobiakjlppafcdimnfho '0.0')
> 介绍: 1、在Google，百度，必应，Rambler，雅虎和好搜等搜索引擎间进行快捷切换，搜索关键词无需重输。
> 2、当Google搜索结果页面跳转中断时，支持Google引用页重试直接访问。
> 3、支持自定义的搜索引擎切换。
> 4、支持设置单击图标来切换搜索引擎。
> 5、支持快捷键切换搜索引擎，默认切换前一个（Ctrl+Shift+Y）、后一个（Ctrl+Shift+U）。
> 6、支持数据云同步，可手动备份和恢复数据。

### [Gliffy Diagrams - Chrome Web Store](https://chrome.google.com/webstore/detail/bhmicilclplefnflapjmnngmkkkkpfad '0.0')
>介绍: Create any diagram in just a few clicks. The Gliffy diagramming App is easy to use and even WORKS OFFLINE.
> 
>You’ll find shapes to create:
>
>·      flowcharts
>·      org charts
>·      UML
>·      ERD
>·      network diagrams
>·      UI
>·      more
>
> 
>You can save Gliffy Diagrams in JPEG, and PNG formats and add them to Google Docs, presentations, wikis or webpages. Create a diagram to:
>
> 
>·      Illustrate the flow of data
>·      Improve communication
>·      Clarify a new process
>·      Document an existing process
>·      Show key relationships within an org
>·      Expose potential process bottlenecks
>
> 
>CLICK THE  "+ FREE"  BUTTON ABOVE AND START DRAWING
> 
>Need help? Shoot us an email at support@gliffy.com 
> 
>REVIEWS:
>PC Magazine says: “For personal use, small business and particularly for network admins who need quick and easy diagram-making, Gliffy is very good.”
> 
>ZDNet says: “Gliffy is a popular and less costly alternative to Microsoft Visio. It is mostly used in planning and documenting software development, business processes and organization charts, with an emphasis on functional business graphics such as diagrams, flowcharts and wireframes.”

### [DuckDuckGo for Chrome - Chrome Web Store](https://chrome.google.com/webstore/detail/bkdgflcldnnnapblkhphbgpggdiikppg '0.0')
> 介绍: DuckDuckGo is the search engine that doesn't track you. Ever.
> • We don’t store your personal information
> • We don’t follow you around with ads.
> • We don't track you in or out of private browsing mode.
> 
> This extension makes DuckDuckGo your default search engine in Chrome and includes some other useful features:
> • Search DuckDuckGo via the right-click menu.
> • Easy access to !bangs via a toolbar button.
> 
> Also check out these pages for more info on DuckDuckGo:
> • About: https://duckduckgo.com/about/
> • Privacy: https://duckduckgo.com/privacy/
> • !bangs: https://duckduckgo.com/bang
> 
> If you're technically inclined, the code for the extension is open source and can be found here: https://github.com/duckduckgo/chrome-zeroclickinfo. We'd appreciate submitting Github issues there for bug/improvement ideas.
> 
> Thank you for using DuckDuckGo!

### [Octotree - Chrome Web Store](https://chrome.google.com/webstore/detail/bkhaagjahfmjljalopjnoealnfndnagc '0.0')
> 介绍: Extension to show code tree for GitHub and GitLab.
> 
> Features:
> * Easy-to-navigate code tree like IDEs
> * Support private repositories
> * Support GitHub and GitLab Enterprise
> 
> Learn more about Octotree settings: https://github.com/buunguyen/octotree#settings
> 

### [New Tab Startup Quotes - Chrome Web Store](https://chrome.google.com/webstore/detail/bljnhgkajocmhlflgefahihojeajhjji '0.0')
> 介绍: With new quotes added every week, this extension will display an inspirational quote that anyone in the startup or business world can appreciate. If you would like to submit a new quote, simply tweet @matcarpenter. 

### [RSS Subscription Extension - Chrome Web Store](https://chrome.google.com/webstore/detail/bmjffnfcokiodbeiamclanljnaheeoke '0.0')
> 介绍: This is a fork of the now discontinued RSS Subscription Extension for Chrome by Google
> 
> With the announcement of the end of Google Reader, Google removed their RSS Subscription Extension from the Chrome webstore.
> 
> This fork removes the previous list of rss readers (Google Reader, iGoogle, My Yahoo) and replaces them with modern well supported web-based RSS readers (Feedly, NewsBlur and The Old Reader)
> 
> The code is open-source and now hosted on github:
> * https://github.com/justinkelly/chrome-rss
> 
> 

### [Set Character Encoding - Chrome Web Store](https://chrome.google.com/webstore/detail/bpojelgakakmcfmjfilgdlmhefphglae '0.0')
> 介绍: Right-click at somewhere on web page to manually set character encoding. The selected character set will automatically apply to all pages on the same site. Select "Use page default" to cancel it. This extension modifies http response headers to override original character set, so when installing Chrome will say "it can read and change all your data on the websites you visit". Just let it go because that is exactly how it works. 
> Starting from V0.4, it supports changing encoding of local files, but you need check 'Allow access to file URLs' in extension manage page.
> To anybody who reports "not working", please share the URL of the page that is not working. We will try our best to make it work for you.

### [Advanced Font Settings - Chrome Web Store](https://chrome.google.com/webstore/detail/caclkomlalccbpcdllchkeecicepbmbm '0.0')
> 介绍: This extension allows you to customize font settings for different language scripts. For example, you can set the default font for Simplified Chinese content to be different than the font for Japanese content. The settings are per-script (as specified in ISO 15924) rather than per-language. For example, there is a single setting for Cyrillic script rather than separate ones for Russian, Ukrainian, etc.
> 
> Chrome will use the font settings controlled by this extension when BOTH of the following are true:
> 1) The web page has declared the language of the content (e.g., by using the HTML lang attribute); and
> 2) The web page has not specified a font to use.
> 
> To use this extension, add it to Chrome and then go to chrome://extensions and click on the "Options" link for this extension.

### [Anything to QRcode - Chrome Web Store](https://chrome.google.com/webstore/detail/calkaljlpglgogjfcidhlmmlgjnpmnmf '0.0')
> 介绍: ===2016/11/11 update v1.1.2 ===
> [bugfix] context menus disappear sometimes
> 
> ===2016/5/12 update v1.1.1 ===
> Fix Chinese decode error
> 
> === update v1.1.0 ===
> Add a "Copy" button to decode result
> 
> === update v1.0.6 ===
> QR Code image decode is supported
> 
> === update v1.0.5 ===
> You can save the qr code image to local disk now :-)
> 
> Anything to QR Code ( local and offline, no long-live background pages, no ads ) : the url of current page, any text/image/link in the page, etc. 
> 
> Contact me: indooorsman@gmail.com

### [Copy URL+ - Chrome Web Store](https://chrome.google.com/webstore/detail/capojgaalppngkaagaobmigigcgnidmn '0.0')
> 介绍: Key features
> 
> - Keyboard shortcuts
> 
> - Flexible context menus
> 
> - URL shortening
> 
> - Notifications
> 
> Icons and promotional images are designed by Honeshabri.

### [Form Fuzzer - Chrome Web Store](https://chrome.google.com/webstore/detail/cbpplldpcdcfejdaldmnfhlodoadjhii '0.0')
> 介绍: This is a fuzz testing, http://en.wikipedia.org/wiki/Fuzz_testing, utility I created to assist in populating web forms with some random data.
> 
> v1.0
> -Fields can be populated with a predefined sequence of characters.
> -Radio buttons are automatically selected. Selects the last one in the group.
> -Checkbox fields can be toggled on or off.
> -The index of drop down list items to be selected can be configured. 
> -No drop down multi-selection.
> 
> v1.0.1
> -New icons. The last ones were... Fuzzy!
> 
> v1.2
> -Added a button to select random characters for the template in the option settings.
> -New defaults: 100 characters for max field size, new field highlight color.
> -Option page has been rebuilt and option items are now grouped somewhat logically.
> -The options page now includes the ability to find tabs open by the current window. These tabs can then be selected to display a list of form input fields of text, hidden or password type. These inputs can then in turn be used to populate named overrides, or named overrides can be set by skipping the tab/input discovery steps and typing in the name. A named override name is accompanied by override values that cause the fuzz step to be skipped and instead uses the value assigned to that override to by-pass any validated input and allow other fields with weaker validation to be targeted.
> 
> v1.3
> -Added the option to select different categories of characters that will be randomly selected from instead of using a template to populate form fields.
> -New icons, again.
> 
> v1.4
> -Added support for textarea fields. These are populated with a template that can be enabled/disabled separately from other types of inputs.
> -Added an option to turn off the auto-selecting of radio buttons.
> -In addition to the testing of password and hidden fields these can now be turned into 'text' type inputs.
> -TEXTAREA and INPUT tags are now case insensitive - some attribute types still have case sensitivity issues!
> 
> Test data is customizable and the options allow configuration of field lengths, checkbox and hidden fields, drop down lists etc.
> 
> *****
> 
> Thanks all for the positive comments and useful feedback and suggestions. I haven't really been paying much attention to this extension lately but have taken some time today to incorporate some of your excellent ideas. As of the last update (v1.4) you should find a few new things that hopefully improve the overall usefulness of the extension. These features are probably not implemented to the extent you would expect (or hope for) but at least they helped me re-familiarize myself with the code again. I will try to provide more frequent updates in the future.
> 
> 

### [Saladict - Chrome Web Store](https://chrome.google.com/webstore/detail/cdonnmffkdaoajfknoeeecmchibpmkmg '0.0')
> 介绍: Urban dictionary, Vocabulary.com, Etymonline, Longman Bussiness, Howjsay and more!
> Highly configurable, PDF support, search history, new-word list, and... it's open-sourced!
> If you enjoy this extension please take a moment to rate it ♥.
> 
> 
> 用爽了可以给个好评哦！感谢打赏咖啡的朋友们。
> 详细使用说明访问 https://github.com/crimx/crx-saladict/wiki
> 
> 有什么问题请在反馈页及时反映，服务器升级什么的很正常，请不要养成随手差评的习惯！商店反馈页面经常出问题，建议到 https://github.com/crimx/crx-saladict/issues 反馈。反馈前建议先点击结果左上词典图标跳转到词典页面判断是否为网络问题。
> 
> 功能一览：
> 1. 多词典支持，英汉、英英、俚语、词源、权威例句、汉语（繁简）、释义分布图、谷歌翻译
> 2. 支持四种划词方式，支持 iframe 划词
> 3. 支持谷歌和有道分级网页翻译
> 4. 查词面板可钉住可拖动可输入
> 5. 支持自动发音
> 6. 支持添加生词与记录查词历史
> 7. 支持 PDF 划词
> 8. 各个词典面板支持个性化调整
> 9. 三按 ctrl 快速查词
> 10. 点击图标快速查词
> 11. 查词结果支持导出图片
> 12. 可显示当前页面二维码
> 13. 右键并支持更多词典页面直达
> 

### [Ex绅士助手 - Chrome Web Store](https://chrome.google.com/webstore/detail/ceegklpccealjoabgpkjjmobjoogddgk '0.0')
> 介绍: 用于快捷下载ex绅士的内容...在您没有credit的时候..
> 1.使用方式直接下载.  会让浏览器大量下载图片....似乎效果并不好.
> 2.生成一大堆链接..交给迅雷吧~这样你还可以做成文件夹..来操作.
> 3.便捷搜索功能...
> 本来想增加自动复制功能的..但是会覆盖掉用户的剪辑版...不是特别好...就算了.

### [SimpleTabOrder - Chrome Web Store](https://chrome.google.com/webstore/detail/cekafjbmkfofacenifehbglhmajimhjf '0.0')
> 介绍: Simple series number 5! 
> 
> This time its a simple tab order customizer. 
> Features include: 
> - change the placement of new tabs 
> - change the tab to focus on when the active tab closes 
> - event page enabled, only loads when needed Updated changelog is in the extension option pages. 
> 
> 
> Reason For Permission Requests: 
> Your tabs and browsing activity 
> -> WHY: Required for use of the chrome.tabs API to obtain tab status, details and also affect tab placement.
> 
> 
> Note: 
> Though the extension still in an early stage so there may still be bugs I've missed. Please do feedback when something is not working, better if there are steps to replicate the problem. Thanks :)

### [JSONView - Chrome Web Store](https://chrome.google.com/webstore/detail/chklaanhfefbnpoihckbnefhakgolnmc '0.0')
> 介绍: JSONView port for Chrome.
> 
> Original firefox extension is here: http://benhollis.net/software/jsonview/ 
> 
> Notes: 
>  - JSON is validated using a client-side javascript implementation of JSONLint (http://github.com/zaach/jsonlint)
>  - this extension displays JSON text compliant with rfc 4627 (http://www.ietf.org/rfc/rfc4627.txt).
>  - JSONP (http://en.wikipedia.org/wiki/JSON#JSONP) is supported
> 
> 
> 
> You can configure JSON parsing method in options page:
> - the default method (JSON content is extracted from displayed page) is faster but can (in some rare cases) alter or fail to parse the JSON content.
> - the safe method costs an extra XMLHttpRequest request (JSON content is extracted from the HTTP response) but is 100% safe.

### [有道智能翻译 by PUBU.IM - Chrome Web Store](https://chrome.google.com/webstore/detail/chpeaiibggkmaongjphijmielpkokcdg '0.0')
> 介绍: 由 瀑布IM 优化过的有道云翻译插件，支持 HTTPS 页面，将更多的资源放在插件内，快速提供翻译，为阅读英文文章提供便利。
> 
> 主要功能包括：
> 
> * 划词翻译
> * 自动翻译全文（入门 -> 进阶 -> 专家 -> 全文） 
> 
> （PS: 翻译技术由有道云翻译提供 http://fanyi.youdao.com，瀑布IM 仅仅做了插件的优化）

### [OneTab - Chrome Web Store](https://chrome.google.com/webstore/detail/chphlpgkkbolifaimnlloiipkdnihall '0.0')
> 介绍: Whenever you find yourself with too many tabs, click the OneTab icon to convert all of your tabs into a list. When you need to access the tabs again, you can either restore them individually or all at once.
> 
> When your tabs are in the OneTab list, you will save up to 95% of memory because you will have reduced the number of tabs open in Google Chrome.
> 
> Privacy assurance
> 
> Information about your tabs are never transmitted or disclosed to the OneTab developers. The only exception to this is if you intentionally click on our 'share as a web page' feature that allows you to upload your list of tabs into a web page in order to share them with others. Tabs are never shared unless you specifically use the 'share as a web page' button. 
> 
> Additional Benefits
> 
> Depending on how many scripts are running inside your tabs, moving them to OneTab can also speed up your computer by reducing the CPU load. We have also had reports that this also contributes to your computer resuming from sleep more quickly.
> 

### [SECAPPS - Chrome Web Store](https://chrome.google.com/webstore/detail/cimdepkgkehkfalgddeedonnjaciffga '0.0')
> 介绍: ｢ This is the SECAPPS Browser Extension for Google Chrome ｣
> 
> This extension provides several special purpose APIs to some web applications hosted by secapps.com. For example, using this extension you will be able to send and receive web requests unrestricted (without the same origin policy rules) from applications such as our Rest client, the Fuzzer and the web security scanner.
> 
> Without this extension, some SECAPPS application will not be able to work within the context of the traditional browser environment.

### [search-engine-filter - Chrome Web Store](https://chrome.google.com/webstore/detail/clkhhmchimakdcfbdohhnkjlljkimmgi '0.0')
> 介绍:  百度搜索,谷歌搜索默认过滤掉脚本之家(www.jb51.net ) 的内容
>  添加一个输入框，输入指定的url，使得在搜索时，来屏蔽掉来自特定地址的内容
>  添加完成后点击过滤按钮进行提示

### [Gloria - Chrome Web Store](https://chrome.google.com/webstore/detail/cnelmenogjgobndnoddckekbojgginbn '0.0')
> 介绍: A programmable website notifications aggregator in Chrome.
> 
> Crawl new content on the site through a custom task code, and pop-up notification alerts you.
> 
> Feel the flow of information, and never miss new messages.
> 
> Read the guide and start enjoy it.
> 
> Tasks Sharing: https://gloria.pub/
> 
> Usage / Document: http://docs.gloria.pub/
> 
> Changelog: http://docs.gloria.pub/changelog.html
> 
> Github: https://github.com/BlackGlory/Gloria

### [I'm Feeling Lucky - Chrome Web Store](https://chrome.google.com/webstore/detail/cnlabakikmdekpfaflaihcepfkjopgll '0.0')
> 介绍: Access Google's 'I'm Feeling Lucky' from Chrome's address bar.
> 
> 1. Type '\' and press the TAB key to invoke the extension.
> 2. Type your search keywords.
> 3. Get directed to Google's top search result for that query.

### [Codota - Chrome Web Store](https://chrome.google.com/webstore/detail/cnpdaoipdfbkpdbdpmceeejdaabiebcb '0.0')
> 介绍: Turns your browser into a powerful code viewer that brings android and java code snippets to life. Codota analyzes code snippets in web pages and helps read, understand and save the code.
> 
> * Shows the API docs for code and XML elements
> * Highlights references for vars
> * Warns about deprecated APIs
> * Finds great related code examples
> * Saves snippets you like in your CodeBox
> * Android code example search directly from Chrome address bar (see screenshots)
> 
> Currently supported sites:
> * StackOverflow.com
> * GitHub.com (public repos only)
> * developer.android.com
> * vogella.com
> * androidexample.com
> * javacodegeeks.com
> Many more will follow soon... please feel free to suggest more sites here in the comments!
> 

### [CaretTab - New Tab Clock and Date - Chrome Web Store](https://chrome.google.com/webstore/detail/cojpndognjdcakkimaloeealehpkljna '0.0')
> 介绍: CaretTab is completely FREE with NO ADS!
> 
> Features:
> ✔ Display time and date on new tab page.
> ✔ Digital/Analog clock options.
> ✔ Add additional clocks with labels.
> ✔ Customizable timezones for all clocks.
> ✔ Search Google/Bing/Baidu and more from new tab page.
> ✔ Display favorite links for quick access.
> ✔ Include a custom message on the page.
> ✔ Choose from a several different color themes or choose your own custom colors.
> ✔ Select your desired size.
> ✔ Choose from a handful of fonts.
> ✔ Customize everything! Toggle the time, seconds, time format, date, date format, search engine, 24 hour time, week numbers, tab title and more.
> ✔ Chrome Sync support. Keep your settings across all devices. (Requires storage permissions)
> ✔ Localized into: English, French, Chinese (Simplified &amp; Traditional), Japanese, German.
> ✔ Also available on Firefox 57+!
> 
> Have any suggestions? Let me know on Twitter @BlueCaret
> 
> CaretTab was designed and developed by BlueCaret
> 
> http://bluecaret.com/project/carettab

### [ToolCat - Chrome Web Store](https://chrome.google.com/webstore/detail/coppgeobilocdhiclhgmadabblhfjgpm '0.0')
> 介绍: 工具喵 / ToolCat（开发常用工具）
> 
> 目前支持以下功能：
> Unix时间戳转换
> URL编码/解码
> IP地址查询
> MD5加密
> BASE64编码/解码
> 随机字符串生成

### [v2ex plus - Chrome Web Store](https://chrome.google.com/webstore/detail/daeclijmnojoemooblcbfeeceopnkolo '0.0')
> 介绍: * 帖子会话详细.
> * 帖子列表主题预览.
> * 只看楼主功能.
> * 楼主回复背景色高亮(颜色可自定义).
> * 感谢爱心颜色自定义.
> * 插入表情与图片(weibo或imgur).
> * 回复内图片旋转.
> * 一键签到与自动签到.
> * 新消息通知提醒并改变扩展按钮颜色.
> 
> One more thing... ^-^
> 
> 
> 
> 源码请见♥: github.com/sciooga/v2ex-plus
> 
> 反馈问题请 Email: sciooga#gmail.com

### [BuiltWith Technology Profiler - Chrome Web Store](https://chrome.google.com/webstore/detail/dapjbgnjinbpoindlpdmhochffioedbn '0.0')
> 介绍: The BuiltWith Chrome Extension lets you find out what a website is built with by a simple click on the builtwith icon!
> 
> BuiltWith is a web site profiler tool. Upon looking up a page, BuiltWith returns all the technologies it can find on the page. BuiltWith’s goal is to help developers, researchers and designers find out what technologies pages are using which may help them to decide what technologies to implement themselves.
> 
> BuiltWith technology tracking includes widgets (snap preview), analytics (Google, Nielsen), frameworks (.NET, Java), publishing (WordPress, Blogger), advertising (DoubleClick, AdSense), CDNs (Amazon S3, Limelight), standards (XHTML,RSS), hosting software (Apache, IIS, CentOS, Debian).
> 
> 
> Changelog
> =-=-=-=-=
> Version 2.6
> Fixes security policy bug that fixes advanced tab.
> 
> Version 2.5
> Supports 'relationships' tab showing relationships between websites.
> 
> Version 2.4
> Power users rejoice - preferences allow you to hide links and descriptions.
> 
> Version 2.3
> Now supports HTTPS lookups.
> 
> 
> 
> 

### [Vimium - Chrome Web Store](https://chrome.google.com/webstore/detail/dbepggeogbaibhgnhhndojpepiihcmeb '0.0')
> 介绍: *NOTE* Google does not allow Vimium to run on this Chrome Web Store page and the Chrome New Tab page, by design. Sorry about that!
> 
> *NOTE* Chrome has some alarmist messaging around the permissions that Vimium needs to run. Really all it's asking for is that Vimium's javascript be loaded into every page. Don't be alarmed. Vimium never talks to any servers and does absolutely nothing with your data. Read the open source code if you're curious.
> 
> For more information about rebinding your keys and how to use many of Vimium's features, see here: https://github.com/philc/vimium/blob/master/README.md
> 
> Modifier keys are specified as <c-x>, <m-x>, <a-x> for ctrl+x, meta+x, and alt+x respectively.
> 
> Navigating the current page:
> 
>     ?       show the help dialog for a list of all available keys
>     h       scroll left
>     j       scroll down
>     k       scroll up
>     l       scroll right
>     gg      scroll to top of the page
>     G       scroll to bottom of the page
>     d       scroll down half a page
>     u       scroll up half a page
>     f       open a link in the current tab
>     F       open a link in a new tab
>     r       reload
>     gs      view source
>     i       enter insert mode -- all commands will be ignored until you hit esc to exit
>     yy      copy the current url to the clipboard
>     yf      copy a link url to the clipboard
>     gf      cycle forward to the next frame
> 
> Navigating to new pages:
> 
>     o       Open URL, bookmark, or history entry
>     O       Open URL, bookmark, history entry in a new tab
>     b       Open bookmark
>     B       Open bookmark in a new tab
> 
> Using find:
> 
>     /       enter find mode -- type your search query and hit enter to search or esc to cancel
>     n       cycle forward to the next find match
>     N       cycle backward to the previous find match
> 
> Navigating your history:
> 
>     H       go back in history
>     L       go forward in history
> 
> Manipulating tabs:
> 
>     J, gT      go one tab left
>     K, gt      go one tab right
>     g0         go to the first tab
>     g$         go to the last tab
>     t          create tab
>     x          close current tab
>     X          restore closed tab (i.e. unwind the 'x' command)
>     T          search through your open tabs
> 
> Additional advanced browsing commands:
> 
>     ]]      Follow the link labeled 'next' or '>'. Helpful for browsing paginated sites.
>     [[      Follow the link labeled 'previous' or '<'. Helpful for browsing paginated sites.
>     <a-f>   open multiple links in a new tab
>     gi      focus the first (or n-th) text input box on the page
>     gu      go up one level in the URL hierarchy
> 
> Vimium supports command repetition so, for example, hitting '5t' will open 5 tabs in rapid succession. ESC (or <c-[>) will clear any partial commands in the queue and will also exit insert and find modes.
> 
> 1.60 (2017-09-14)
> 
> - Features:
>     - There's a new (advanced) option to ignore the keyboard layout; this can
>       be helpful for users of non-Latin keyboards.
>     - Firefox support.  This is a work in progress.
> 
> - Bug fixes:
>     - Fixed issue affecting hint placement when the display is zoomed.
>     - Fixed search completion for Firefox (released as 1.59.1, Firefox only).
> 
> 1.59 (2017-04-07)
> 
> - Features:
>      - Some commands now work on PDF tabs (J, K, o, b, etc.). Scrolling and other content-related commands still do not work.
> 
> Changes in 1.58 (2017-03-08)
> 
> - Features:
>     - The `createTab` command can now open specific URLs (e.g, `map X createTab http://www.bbc.com/news`).
>     - With pass keys defined for a site (such as GMail), you can now use Vimium's bindings again with, for example, `map \ passNextKey normal`;
>       this reactivates normal mode temporarily, but *without any pass keys*.
>     - You can now map multi-modifier keys, for example: `<c-a-X>`.
>     - Vimium can now do simple key mapping in some modes; see
>       [here](https://github.com/philc/vimium/wiki/Tips-and-Tricks#key-mapping).
>       This can be helpful with some non-English keyboards (and can also be used
>       to remap `Escape`).
>     - For *Custom key mappings* on the options page, lines which end with `\` are now continued on the following line.
> - Process:
>     - In order to provide faster bug fixes, we may in future push new releases without the noisy notification.
> 
> - Post-release minor fixes:
>     - 1.58.1 (2017-03-09) fix bug in `LinkHints.activateModeWithQueue` (#2445).
>     - 1.58.2 (2017-03-19) fix key handling bug (#2453).
> 
> Changes in v1.57 (2016-10-01)
> 
> - New commands:
>     - `toggleMuteTab` - mute or unmute the current tab (default binding
>       `<a-m>`).
> - Other new features:
>     - You can now map `<backspace>` to a Vimium command (e.g. `map <backspace> goBack`).
>     - For link hints, when one hint marker is covered by another, `<Space>` now
>       rotates the stacking order.  If you use filtered hints, you'll need to
>       use a modifier (e.g. `<c-Space>`).
> - Changes:
>     - Global marks now search for an existing matching tab by prefix (rather than exact match).
>       This allows global marks to be used as quick bookmarks on sites (like Facebook, Gmail, etc)
>       where the URL changes as you navigate around.
> - Bug fixes:
>     - `/i` can no longer hang Vimium while the page is loading.
>     - `<c-a-[>` is no longer handled (incorrectly) as `Escape`.  This also affects `<Alt-Gr-[>`.
>     - If `goX` is mapped, then `go` no longer launches the vomnibar.  This only affects three-key (or longer) bindings.
> 
> 1.61 (2017-10-27)
> 
> For filtered hints, you can now now use alphabetical hint characters instead of digits; use <Shift> for hint characters.
> With map R reload hard, the reload command now asks Chrome to bypass its cache.
> You can now map <c-[> to a command (in which case it will not be treated as Escape).
> Various bug fixes, particularly for Firefox.
> 1.60 (2017-09-14)
> 
> Features:
> 
> There's a new (advanced) option to ignore the keyboard layout; this can be helpful for users of non-Latin keyboards.
> Firefox support. This is a work in progress; please report any issues here; see the add on.
> Bug fixes:
> 
> Fixed issue affecting hint placement when the display is zoomed.
> Fixed search completion for Firefox (released as 1.59.1, Firefox only).
> Minor versions:
> 
> 1.60.1: fix #2642.
> 1.60.2: revert previous fix for HiDPI screens. This was breaking link-hint positioning for some users.
> 1.60.3: fix link-hint positioning.
> 1.60.4: fix hints opening in new tab (Firefox only).
> 1.59 (2017-04-07)
> 
> Features:
> Some commands now work on PDF tabs (J, K, o, b, etc.). Scrolling and other content-related commands still do not work.
> 1.58 (2017-03-08)
> 
> Features:
> 
> The createTab command can now open specific URLs (e.g, map X createTab http://www.bbc.com/news).
> With pass keys defined for a site (such as GMail), you can now use Vimium's bindings again with, for example, map \ passNextKey normal; this reactivates normal mode temporarily, but without any pass keys.
> You can now map multi-modifier keys, for example: <c-a-X>.
> Vimium can now do simple key mapping in some modes; see here. This can be helpful with some non-English keyboards (and can also be used to remap Escape).
> For Custom key mappings on the options page, lines which end with \ are now continued on the following line.
> Process:
> 
> In order to provide faster bug fixes, we may in future push new releases without the noisy notification.
> Post-release minor fixes:
> 
> 1.58.1 (2017-03-09) fix bug in LinkHints.activateModeWithQueue (#2445).
> 1.58.2 (2017-03-19) fix key handling bug (#2453).
> 1.57 (2016-10-01)
> 
> New commands:
> toggleMuteTab - mute or unmute the current tab (default binding <a-m>), see also advanced usage.
> Other new features:
> You can now map <backspace> to a Vimium command (e.g. map <backspace> goBack).
> For link hints, when one hint marker is covered by another, <Space> now rotates the stacking order. If you use filtered hints, you'll need to use a modifier (e.g. <c-Space>).
> Changes:
> Global marks now search for an existing matching tab by prefix (rather than exact match). This allows global marks to be used as quick bookmarks on sites (like Facebook, Gmail, etc) where the URL changes as you navigate around.
> Bug fixes:
> /i can no longer hang Vimium while the page is loading.
> <c-a-[> is no longer handled (incorrectly) as Escape. This also affects <Alt-Gr-[>.
> If goX is mapped, then go no longer launches the vomnibar. This only affects three-key (or longer) bindings.
> 1.56 (2016-06-11)
> 
> Vimium now works around a Chromium bug affecting users with non-standard keyboard layouts (see #2147).
> Fixed a bug preventing visual line mode (V) from working.
> 1.55 (2016-05-26)
> 
> New commands:
> visitPreviousTab - visit the previous tab (by recency) with ^, or the tab before that with 2^.
> passNextKey - pass the next key to the page. For example, using map <c-]> passNextKey, you can close Facebook's messenger popups with <c-]><Esc>.
> Link hints:
> Now work across all frames in the tab.
> Now select frames and scrollable elements.
> Now accept a count prefix; 3F opens three new background tabs, 999F opens many tabs.
> For filtered link hints, a new option on the settings page requires you to press Enter to activate a link; this prevents unintentionally triggering Vimium commands with trailing keystrokes.
> Miscellaneous:
> gg now accepts a count prefix.
> W now accepts a count prefix; 3W moves three tabs to a new window.
> With smooth scrolling, 2j-and-hold now gives a faster scroll than j-and-hold.
> You can now bind keys to a command with a defined count prefix; for example, map d scrollDown count=4.
> You can now bind three-key (or longer) sequences; for example, map abc enterInsertMode.
> c-y and c-e now scroll in visual mode.
> The Vimium help dialog has been re-styled.
> Bug fixes:
> <c-a-[> is no longer treated as escape.
> Fix icon display and memory leak due to a regression in recent Chrome versions (49+).
> For web-devs only:
> When disabled on a tab, Vimium no longer pollutes the dev console with network requests.
> 
> Changes in v1.56 (2016-06-11)
> 
> Bug fixes.
> 
> Changes in v1.55 (2016-05-26)
> - New commands:
>     - `visitPreviousTab` - visit the previous tab (by recency) with `^`
>     - `passNextKey` - pass the next key to the page.
> - Link hints:
>     - Now work across all frames in the tab.
>     - Now select frames and scrollable elements.
>     - Now accept a count prefix; `3F` opens three new background tabs, `999F` opens many tabs.
>     - For filtered link hints, a new option on the settings page requires you to press `Enter` to activate a
>       link; this prevents unintentionally triggering Vimium commands with trailing keystrokes.
> - Miscellaneous:
>     - `gg` now accepts a `count` prefix.
>     - `W` now accepts a count prefix; `3W` moves three tabs to a new window.
>     - With smooth scrolling, `2j`-and-hold now gives a faster scroll than `j`-and-hold.
>     - You can now bind keys to a command with a defined count prefix; for example, `map d scrollDown count=4`.
>     - You can now bind three-key (or longer) sequences; for example, `map abc enterInsertMode`.
>     - `c-y` and `c-e` now scroll in visual mode.
>     - The Vimium help dialog has been re-styled.
> - Bug fixes:
>     - `<c-a-[>` is no longer treated as escape.
> - For web-devs only:
>     - When disabled on a tab, Vimium no longer pollutes the dev console with network requests.
> 
> To see older release notes, go to:
> https://github.com/philc/vimium/blob/master/README.md

### [Site Spider - Chrome Web Store](https://chrome.google.com/webstore/detail/ddlodfbcplakmddhdlffebcggbbighda '0.0')
> 介绍: Use this extension to spider a website looking for dead links.  One can restrict the spidering to a directory, a domain, or any other regular expression.  The spider can also follow one link beyond this restriction, allowing one to find broken external links.
> 
> Usage: Install the plugin.  Go to the page you want to start from.  Click the spider icon in your toolbar.  Set the restriction regular expression and go.  To cancel a spidering session before it has finished, just close its results tab.
> 
> Security: Because this is a client-side spider, it uses your own authentication to access pages.  Thus it can go wherever you have access to go.  This plugin does not log any data or "phone home" in any way.  It is completely open source.
> 

### [网易邮箱 - Chrome Web Store](https://chrome.google.com/webstore/detail/degnllcmhlfjedphgljfbgjcdijpagpp '0.0')
> 介绍: 功能介绍
> 
> 一键登录网易邮箱：
> 绑定网易邮箱帐号后，点击图标即可直接进入网易邮箱
> 
> 新邮件即时提醒：
> 当有新邮件时，会显示主题和发件人，以飘窗的形式提醒您查看，如果想了解邮件详细内容，您可以直接点击飘窗进入邮箱读信。同时，在插件栏会显示未读邮件数量，确保不让您错过任何一封重要邮件。
> 
> 同时管理多个网易邮箱：
> 可同时管理3个网易邮箱，不管是工作邮箱还是私人邮箱，都可轻松搞定。
> 
> 用户反馈（将链接复制到浏览器中打开）：
> http://zhidao.mail.163.com/zhidao/newsugg.jsp#chrome应用

### [Copy URL + Title - Chrome Web Store](https://chrome.google.com/webstore/detail/dgagjmdgbakclelfacghmmbadkdegjjh '0.0')
> 介绍: Features:
> 
> * Copy Page URL
> * Copy Page Title
> * Copy Page HTML Link
> * Copy Page Title and URL
> 
> * Copy URL of all Tab
> * Copy Title of all Tab
> * Copy HTML Link of all Tab
> * Copy Title and URL of all Tab
> 
> Also available for Opera from https://addons.opera.com/en/extensions/details/copy-url-title/
> 

### [Local CDN - Chrome Web Store](https://chrome.google.com/webstore/detail/dgfedofdiaapcideaajjaklpmdpcdapg '0.0')
> 介绍: Local CDN extension is a fork for Decentraleyes project by @Synzvato. It brings local redirection for well-known libraries. After the extension is installed, when a known library is requested by a webpage, the extension redirects this request to a local equivalent and updates the badge number. Hovering over the toolbar displays the name of libraries that have been redirected for the current page. Note that since this resource is fetched locally, you should also experience faster page loading. 
> 
> To see the list of supported libraries, please visit the FAQs page.
> 
> For FAQs please visit:
> http://add0n.com/local-cdn.html
> 
> For bug reports please visit:
> https://github.com/james-fray/local-cdn/
> 
> --0.1.2
> Local CDN does not use Decentraleyes code any more
> --0.1.3
> All libraries are re-fetched from CND sources.
> Code has been optimized for performance improvement.
> 

### [Copy As Markdown - Chrome Web Store](https://chrome.google.com/webstore/detail/dgoenpnkphkichnohepecnmpmihnabdg '0.0')
> 介绍: Just select HTML in your page and then click the the 'M' icon in the extension toolbar, then the markdown content is in your clipboard. Cool?
> 
> Also, you can use the shortcut of the extension, `Alt + C` for Windows or `Option + C` for Mac or define yourself. Enjoy it.
> 
> History：
> 
> 2016.06.21 fix a bug, change relative links to absolute links.

### [wasavi - Chrome Web Store](https://chrome.google.com/webstore/detail/dgogifpkoilgiofhhhodbodcfgomelhe '0.0')
> 介绍: wasavi is a clone of vi editor and extends a TEXTAREA element. 
> If you focus TEXTAREA element and press Ctrl+Enter, TEXTAREA turns into vi editor.
> 
> wasavi supports following vi commands:
> * c y d > < gq cc yy dd >> << C Y D gqq
> * - + ^ <home> $ <end> % | comma(,) ; _ / ? ' ` ( ) { } [[ ]] <enter> 0 j k h l ^N ^P ^H <down> <up> <left> <right> <space> w W b B e E gg gj gk g^ g$ G H M L f F t T n N
> * ^U ^D ^Y ^E ^B ^F <pageup> <pagedown> z<enter> z. zz z-
> * x X <delete> p P J period( . ) u ^R ~ ^L ^G m @ q r R a A i I o O & s S ZZ
> * :
> 
> wasavi supports following ex commands:
> * abbreviate cd chdir copy delete edit file filesystem global join k map mark marks move options print put pwd quit read redo s & ~ set registers to unabbreviate undo unmap version v write wq xit yank > < @ *
> 
> In addition, wasavi ported some functions from vim such as incremental-searching, multi level undo/redo, and text objects.
> 
> Visit http://appsweets.net/wasavi/ for more details and tips.
> Source code of wasavi is hosted on https://github.com/akahuku/wasavi.

### [Tampermonkey - Chrome Web Store](https://chrome.google.com/webstore/detail/dhdgffkkebhmkfjojejmpbldmpobfkfo '0.0')
> 介绍: Tampermonkey is the most popular userscript manager, with over 10 million users.
> 
> Tampermonkey is used to run so called userscripts (sometimes also called Greasemonkey scripts). Userscripts are little computer programs that for example add download buttons to YouTube pages, cleanup your Facebook timeline or help playing an online game.
> 
> Features
> 
>  - manage and edit your userscripts
>  - enable and disable your scripts with 2 clicks
>  - script synchronization via Chrome Sync
>  - backup and restore via zip file and/or cloud storage (Google Drive, Dropbox, OneDrive)
>  - all GM_* functions including (GM_registerMenuCommand, GM_getResourceText, GM_getResourceURL, GM_notification)
>  - a lot of tags supported by Greasemonkey and Scriptish (like @resource, @require, ...)
>  - compatible to Greasemonkey 3.x (experimental 4.x support)
> 
> For a full overview please take a look at the FAQ or just install this extension. ;)
> 
> Thanks for using Tampermonkey. :)
> 
>  Bugs 
> 
> Please DON'T report bugs by a review, BUT HERE:
>  - http://tampermonkey.net/bug
>  - https://github.com/Tampermonkey/tampermonkey/issues
> 
>  Changelog 
> 
> http://tampermonkey.net/changelog.php?ext=dhdg
> 
>  FAQ 
> 
> http://tampermonkey.net/faq

### [Emmet LiveStyle - Chrome Web Store](https://chrome.google.com/webstore/detail/diebikgmpmeppiilkaijjbdgciafajmg '0.0')
> 介绍: Instantly updates your web-page stylesheet while you edit CSS, LESS or SCSS file in your text editor. No file saving or page reloading: pure real-time experience! And this is the first tool that transfers updates from DevTools back into source code the right way.
> 
> Includes Remote View: creates publicly-available URL (aka “reverse tunnel”) to test your local web-sites on any internet-connect device or services like BrowserStack.

Traceback (most recent call last):
### [Error 404 (Not Found)!!1](https://chrome.google.com/webstore/detail/difaidmfnkechmglnihhhehdmjlifbjl '0.0')
  File "/Users/sqsgalaxys/Downloads/MeProjects/untitled1/pythonGetChromeWebstore.py", line 258, in <module>
    print("介绍: " + soup.find_all("pre", class_="C-b-p-j-Oa")[0].text)
IndexError: list index out of range

Process finished with exit code 1




/usr/local/bin/python3.6 /Users/sqsgalaxys/Downloads/MeProjects/untitled1/pythonGetChromeWebstore.py
### [Cntv Live2 Chrome Live Plugin - Chrome Web Store](https://chrome.google.com/webstore/detail/dijmjenapeionhnanhobmdkdfehmdhhl '0.0')
> 
> 介绍: cntv 视频直播chrome扩展程序
> 本扩展暂时只支持windows&&chrome
> 安装本扩展,chrome打开http://live.cntv.cn按提示即可观看cntv视频直播。
> 20151028:change icon & add install check
> > 

### [Google Tasks (by Google) - Chrome Web Store](https://chrome.google.com/webstore/detail/dmglolhoplikcoamfgjgammjbgchgjdd '0.0')
> 介绍: Easily add and manage your tasks from Chrome in one of three ways:
> 
> *  Simply type "t Your new task" into the Chrome Omnibar to easily add a task from whatever web page you're on.
> 
> *  Click the Tasks icon to add a task, see your tasks and task lists and mark a task as completed
> 
> *  Highlight text on any web page, right click and add that text to a new task.
> 
> Tasks are visible everywhere that you can see your Google Tasks - in Gmail, Calendar, iGoogle, Mobile and via the Google Tasks API.
> 
> This extension has been released as an example of the Google Tasks API, and can be viewed and contributed to at https://code.google.com/p/google-tasks-chrome-extension
> 
> Please note that if you sign into multiple Google accounts you should ensure that the first account you sign into is the account you wish to use when managing Tasks via this extension.
> 
> Thanks to Neal Fultz for updating this extension to work with new Google Tasks APIs!
> ### [网易云音乐辅助 - Chrome Web Store](https://chrome.google.com/webstore/detail/dmidlfboljckpijkmbmolidjimmfelho '0.0')
> 介绍: 手机和电脑上一直都用网易云音乐，但是网页版的感觉还是有点不爽， 所以做了这个辅助扩展(chrome).
> 
> 项目地址 https://github.com/kikyous/music.163.com Pull Requests Welcome
> ### [Axure RP Extension for Chrome - Chrome Web Store](https://chrome.google.com/webstore/detail/dogkpdfcklifaemcdfbildhcofnopogp '0.0')
> 介绍: Install this extension to allow the viewing of Axure RP Prototypes from your local hard drive in Google Chrome.
> 
> This extension requires a high access level to allow the viewing of the file:// protocol. This extension only requires these permissions to allow viewing of prototypes in Chrome - Axure does not track or access any of your information.
> 
> IMPORTANT: After installing the extension you must check the setting "Allow access to file URLs". This can be accessed from Tools > Extensions > Axure RP Extension for Chrome.
> 
> You do not have to install this extension if you want to view prototypes hosted on the web. For example, you don't need this to view prototypes from Axure Share (share.axure.com).
> 
> If you have any issues or questions, please email support@axure.com
> ### [Java API Search - Chrome Web Store](https://chrome.google.com/webstore/detail/dphfngjamcomlehblpblaacingmaojnm '0.0')
> 介绍: Use this omnibox plugin to directly search the online Java help.
> 
> Simply type 'Java ' to start your search, then the name of whatever class you are looking for help with, to take you straight to the relevant page in Adobe's online documentation.
> 
> Source from: 
> 
> https://github.com/mpress/developer-omniboxes-for-chrome
> ### [yformater - Chrome Web Store](https://chrome.google.com/webstore/detail/eaomiplfdajdfecncbllnmgbdccdblkf '0.0')
> 介绍: 可能是史上最用心的json格式化插件，集·干净·小巧·睿智·于一身，不信你就试试看！
> 最聪明的chrome json格式化高亮预览插件，彻底抛弃“在线”工具！
> ### [Mortality - New Tab - Chrome Web Store](https://chrome.google.com/webstore/detail/eeedcpdcehnikgkhbobmkjcipjhlbmpn '0.0')
> 介绍: Mortality is a new tab extension that reminds you of your precise age.
> It can also countdown to your death, countdown to a deadline, or show you how many people are older or younger than you globally.
> A bitter-sweet motivational tool; it illustrates how little time we have.
> By default, circles represent months, for the average lifespan of 79 years.
> As you age, the circles fill, and are split into the main Chapters of your life.
> 
> Get busy living, or get busy dying.
> You can never go back :)
> 
> 
> ### [CL1024 - Chrome Web Store](https://chrome.google.com/webstore/detail/efdllnloheadnjjahfmdohomdphlgcjm '0.0')
> 介绍: 正版插件
> ### [Readwise - Chrome Web Store](https://chrome.google.com/webstore/detail/egfepjgjabnppmaiadpedbgadkcelcbd '0.0')
> 介绍: Don't let your highlights disappear. Sync them with Readwise and then review them daily.
> ### [Feedly Notifier - Chrome Web Store](https://chrome.google.com/webstore/detail/egikgfbhipinieabdmcpigejkaomgjgb '0.0')
> 介绍: Feedly notifier is a tiny extension that keeps you up to date with your feedly subscriptions.
> 
> **Features**
> 
> - unread news count
> - unread news headers (with direct link on the news site) in the popup window
> - article preview in the popup window
> - ability to set categories for updates
> - HTTPS support
> - ability to mark news as read
> - ability to save feeds for later reading
> - ability to filter feeds by category in the popup
> - ability to open site on button click (work as a counter only)
> - desktop notifications
> - background mode
> 
> **Translation**
> Help us to translate the extension or improve existing translations.
> https://poeditor.com/join/project?hash=2fZxqOmDJo
> 
> **Changelog**
> 
> https://github.com/olsh/Feedly-Notifier/releases
> 
> **Support**
> 
> If you found a bug or you have a suggestion, please let us know.
> You can report about it here:
> https://github.com/olsh/Feedly-Notifier/issues
> 
> **Source code**
> 
> https://github.com/olsh/Feedly-Notifier
> ### [有道智能翻译 - Chrome Web Store](https://chrome.google.com/webstore/detail/eigkcamclfehonkmfoomgapimelgndlc '0.0')
> 介绍: 阅读理解式的难词注释，提高你的阅读速度；遇到未注释的难词，还可以划词查看释义。（有道网页翻译2.0插件
> ### [Wikiwand: Wikipedia Modernized - Chrome Web Store](https://chrome.google.com/webstore/detail/emffkefkbkpkgpdeeooapgaicgmcbolj '0.0')
> 介绍: As featured on TechCrunch, Lifehacker, Gizmodo, Fast Company and The Next Web:
> 
> Wikiwand is a new award-winning interface that optimizes Wikipedia's amazing content for a quicker and significantly improved reading experience!
> 
> ► New clean layout for optimal readability
> ► Great modern typography
> ► Convenient fixed table-of-contents
> ► Quick preview when hovering over links
> ► Multi-language search with thumbnails
> ► Beautiful, immersive cover photos
> ► Larger photos and better media gallery
> ► Easy article narration and audio playback
> ► Color, font and layout personalization
> ► Dozens of other improvements
> 
> Like Wikiwand? Please rate us ★★★★★
> 
> Q: How do I use Wikiwand?
> A: Just install our light extension and keep using Wikipedia as usual. The Wikiwand interface will automatically appear every time you visit a Wikipedia article.
> 
> Q: How does it work?
> A: It's simple. The extension replaces links to Wikipedia articles with links to the same article on Wikiwand. 
> 
> Q: Can I still read the original article on Wikipedia?
> A: Of course! Click the "Wikiwand" logo, then "Read on Wikipedia"
> 
> Found a bug? Got a suggestion?
> http://bit.ly/wikiwand-support
> ### [qiniu upload files - Chrome Web Store](https://chrome.google.com/webstore/detail/emmfkgdgapbjphdolealbojmcmnphdcc '0.0')
> 介绍: 支持拖拽上传，批量操作，文件处理等功能
> 不断更新中
> ### [Chrome Bing Dict - Chrome Web Store](https://chrome.google.com/webstore/detail/enaoikphbblijoloobmapommnigpocid '0.0')
> 介绍: 超简洁的翻译插件
> 
> 来自必应词典的权威词汇，可自动识别中英互译，并可将翻译结果直接插入到内容之中，在页面中选中词语后按'v'键即可。
> 
> 同时也提供较为详细的分词性查询功能，可以直接在插件中进行查询。
> 
> 此项目于Github开源，欢迎Star：https://github.com/DremyGit/ChromeBingDict
> ### [有道词典Chrome划词插件 - Chrome Web Store](https://chrome.google.com/webstore/detail/eopjamdnofihpioajgfdikhhbobonhbb '0.0')
> 介绍: Chrome浏览器下的有道词典划词翻译扩展插件！让您在Chrome浏览器下更方便的使用有道词典。
> 扩展插件的主要功能如下：
> 
> 1. 划词释义：在浏览的页面上用鼠标划取任意单词，或直接双击任意单词，即可使有道词典查询其详细释义。同时提供音标发音及从海量数据中挖掘出的网络释义，满足你查词的需求。
> 
> 2. 划句翻译：在页面中划取一段文字，插件将自动判别语种，并利用强大的有道翻译引擎给出翻译结果，阅读英文、日文文章不发愁！
> 
> 3. 多语种查询：目前划词翻译支持中英日韩法五种语言，划句翻译支持中英日三种语言，更多语种让您的翻译更自如。
> 
> 4. 主窗口快速查词：支持在插件主窗口内快速查词，即使不开启有道词典客户端，也可使用有道词典Web版助您查看详细释义和更加丰富的内容。
> 
> 5. 新增了“ctrl指词即译”模式，让您取词更快一步！
> 
> 本插件支持Linux，MacOS系统！希望大家喜欢！
> 
> 有道词典Chrome划词插件官网：
> http://cidian.youdao.com/chromeplus/
> 
> 产品论坛：
> http://tie.youdao.com/tl_-5379154985906524281?keyfrom=chrome.extension
> 
> 意见反馈:
> http://feedback.youdao.com/deskapp_report.jsp?prodtype=deskdict&ver=chrome.extension
> 
> *注意：在安装插件时已经打开的页面，必须重启浏览器才能使用取词
>            在Google Chrome Extensions官方网站上无法取词
> 
> 1.27更新 修改了在macos下自动发音的bug
> 1.5更新 支持在线pdf取词；
> 1.5更新 支持自定义发音方式；具体方法，浏览器右上角点击插件图标，点选发音方式。
> 
> ### [PanicButton - Chrome Web Store](https://chrome.google.com/webstore/detail/faminaibgiklngmfpfbhmokfmnglamcm '0.0')
> 介绍: PanicButton makes it easier for you to hide all of your tabs at once just by clicking on a button. They are then saved as bookmarks in a separate folder. Afterwards, the PanicButton turns green and shows you how many tabs are currently hidden.
> 
> Another click on the PanicButton restores all of the tabs you have hidden earlier.
> 
> If you don't want to restore your tabs just delete the "temporary Panic" folder in Chrome's "Other bookmarks"-folder.
> 
> You can also use PanicButton's keyboard shortcut. Just press F4 to hide and restore all your tabs. (currently only works when you're on a http:// or https:// page)
> 
> PanicButton was originally developed by Thomas Greiner (http://twitter.com/ThomasGreiner) and is now part of the HideMyAss.com family of privacy applications
> 
> [ CONTACT US ]
> Twitter: http://twitter.com/hidemyass
> Help:  http://twitter.com/teamHMA
> Email: info@hidemyass.com
> 
> 
> [ HELP MAKING IT BETTER ]
> Just follow the link and star the issue and please do not post comments about PanicButton on there:
> http://code.google.com/p/chromium/issues/detail?id=57074
> (you need to be logged in to your Google account to see the star)
> 
> [ SUGGEST FEATURES ]
> http://www.google.com/moderator/#15/e=26ce2&t=26ce2.40
> 
> Major Version Updates
> 1.0
>   - Brand new design
> 0.14
>    - PanicRoom integration
>    - implemented Content Security Policy
>    - improved user experience and security of options page
>    - portuguese added
>    - many languages updated
> 0.13
>    - advanced password protection added
>    - animated loading icon added
>    - default keyboard shortcut set to F4
>    - improved speed
>    - improved options page
>    - a lot of bug fixes
>    - security vulnerability fixes
>    - catalan, greek, hindi, romanian added
> 0.12
>    - option added: multiple safe pages
>    - improved popup
>    - some bug fixes
>    - languages added: bulgarian, finnish, filipino, latvian
> 0.1 - 0.11 (only most important ones)
>    - many options added
>    - many languages added
>    - background page optimized
>    - script communications improved
> ### [Pokemon NO! Pokemon BLOCKER! - Chrome Web Store](https://chrome.google.com/webstore/detail/fcfkedekimblhldjbiphhfobkafkeaeb '0.0')
> 介绍: Remove all mentions of this annoying trend from your browser!
> 
> Tired of seeing this children's game being discussed in the news, on Twitter and on your Facebook feed? Well now you never have to see it again! Pokemon NO will remove any mention of Pokemon and their new app from any website you visit! 
> 
> Enjoy seeing real news events and important things on your browser again. 
> 
> - Blocks Pokemon references on any site, including Facebook and Twitter
> - No ads or annoying popups! Now and forever! :)
> 
> http://www.twitter.com/theconorbrowne
> ### [Full Page Screen Capture - Chrome Web Store](https://chrome.google.com/webstore/detail/fdpohaocaechififmbbbbbknoalclacl '0.0')
> 介绍: The simplest way to take a full page screenshot of your current browser window. Click on the extension in your browser bar (or press Alt+Shift+P), watch the extension capture each part of the page, and be transported to a new tab of your image that you can right-click to save-as or just drag to your desktop. No bloat, no ads, just a simple way to turn a full web page into an image.
> 
> The only way to screenshot the entire page is to scroll to each visible part, so please be patient as it quickly assembles all the pieces. For the rare scenario where your page is too large for Chrome to store it in one image, it will let you know and split it up into just enough images in separate tabs.
> 
> This is an open source project. Visit the Full Page Screen Capture Github page for more information, bug reports, or to contribute:
> 
> https://github.com/mrcoles/full-page-screen-capture-chrome-extension
> 
> **No extra permissions are required to use this extension.**
> 
> 
> Change Log:
> 
> 2.2 – 2016-09-01 – support for ctrl+s (or cmd+s on Mac) to save the screenshot
> 2.1 — 2016-08-22 — fixed capture zoom in/out issues, add an expand button to capture header
> 2.0 — 2016-08-19 — updated result tab for screenshots with click to download and ability to view/delete your screenshots
> 1.0.1 — 2016-05-14 — fix incognito mode "File not found" bug and better tab handling
> 1.0.0 — 2016-05-09 — this is a major release: introduces keyboard shortcut, splitting of images for pages that are too long, better handling of zoomed/emulator pages, more subtle gray icon, SVG support, and stability fixes (thank you @bluememory14, @BSierakowski, @denilsonsa, and all submitters of bug reports)
> 0.0.15 — 2015-04-05 — add timestamp to images so they are unique paths (via @HetIsNiels) and popup display fix
> 0.0.14 — 2015-02-14 — more “retina” fixes
> 0.0.13 — 2015-01-02 — remove scale feature to hopefully fix bugs experienced on “retina” displays
> 0.0.12 — 2014-08-24 — change permissions to more restrictive “activeTab”
> 0.0.11 — 2014-04-19 — backwards compatible permissions update
> 0.0.10 — 2014-04-17 — fixed permissions issue that prevents screen capture in Chrome 34
> 0.0.9 — 2013-12-08 — fixed bugs when the image is pieced together on retina screens
> 0.0.8 — 2013-11-17 — improved calculation of page width and height on non-standard pages
> 0.0.7 — 2013-10-10 — 10x speed improvement in capture time and restore to original scroll positions after capture (via @terrycojones)
> 0.0.6 — 2013-01-26 — Fixed scenario when captured image can load as a broken icon (caused by loading image before it has been written to the file system)
> 0.0.5 — 2013–01–21 — Fixed small bug in 0.0.4
> 0.0.4 — 2013–01–21 — Replaced deprecated BlobBuilder with Blob (via @gleitz)
> 0.0.3 — 2012-11-25 — Removed need to reload pages that were open before the extension is installed
> 0.0.2 — 2012-11-21 — Better messaging for pages that can't be screen captured (e.g., content scripts cannot run on the chrome webstore), and the generated image now incorporates the URL into its name
> 0.0.1 — 2012-11-06 — Initial release
> 
> ### [Postman - Chrome Web Store](https://chrome.google.com/webstore/detail/fhbjgbiflinjbdggehcddcbncdddomop '0.0')
> 介绍: Postman makes API development faster, easier, and better. The free app is used by more than 3.5 million developers and 30,000 companies worldwide. Postman is designed with the developer in mind, and packed with features and options.
> 
> Postman features include:
> 
> Powerful, simple to use GUI
> Saved history of API requests
> Unlimited collections, environments, tests, and sharing
> Automated testing with collection runner
> Web-viewable, detailed API documentation
> Flexible API monitoring, for uptime, performance, and accuracy
> Mock servers, to support split-stack development
> 
> Note on Permissions:
> The “Your data on all websites” permission is required to send a request to a domain. It's not used for anything else by Postman.
> 
> View the complete Postman EULA at: https://www.getpostman.com/licenses/postman_base_app
> 
> Follow Us:
> Twitter: http://www.twitter.com/postmanclient 
> Facebook: http://www.facebook.com/getpostman
> Join our Slack community: https://www.getpostman.com/slack-invite
> Traceback (most recent call last):
>   File "/Users/sqsgalaxys/Downloads/MeProjects/untitled1/pythonGetChromeWebstore.py", line 259, in <module>
>     print("介绍: " + soup.find_all("pre", class_="C-b-p-j-Oa")[0].text)
> IndexError: list index out of range
> ### [Error 404 (Not Found)!!1](https://chrome.google.com/webstore/detail/fiddahcmipladlobggbjojeimokalcnj '0.0')
> 
> 
> 
> 
> 
> 
> /usr/local/bin/python3.6 /Users/sqsgalaxys/Downloads/MeProjects/untitled1/pythonGetChromeWebstore.py
### [Stylish - Custom themes for any website - Chrome Web Store](https://chrome.google.com/webstore/detail/fjnbnpbmkenffdnngjfgmeleoegfcffe '0.0')
> 介绍: Stylish lets you style the web according to your personal taste.
> 
> ★  Give Reddit a dark mode, use minimalist Facebook themes, or change the look of Google, Twitter and any of your favorite sites
> ★  Customize website backgrounds, color schemes, youtube skins, fonts and even animations
> ★  Easily disable, enable, edit or delete any of your installed styles (themes)
> ★  Create your own user styles (themes) using Stylish’s CSS editor, and share it with millions of Stylish users
>  
> ***Stylish has themes & skins for websites and web apps from all over the world, such as:***
> 
> ✔  Search Engines – Google, Baidu, Yahoo
> ✔  Email – Gmail themes style & personalize your email to your liking
> ✔  Social Networks – Facebook, Twitter, Reddit, Instagram, WeChat, and even Whatsapp themes!
> ✔  Developer Sites – Stackoverflow, Github, JIRA, Thunderbird
> ✔  Browsers – Chrome, Firefox, Opera, Safari, Baidu
> ✔  Youtube Themes – Stream videos night and day with your favorite Youtube skins
> 
> ***Request a Theme***
> If you find a site with has no styles/themes, or you want a new style created based on your favorite artist, movie or holiday, ask the Stylish community to create that theme on the Stylish forum - https://forum.userstyles.org
> 
> ***Contribute a Theme***
> If you know CSS, become a Youtube skins or Facebook theme creator - create and share styles for Facebook, Youtube, and other popular websites.
> 
> ***Stylish Communities***
> ✔  Official: https://forum.userstyles.org
> ✔  https://www.reddit.com/r/userstyles/
> ✔  https://www.tumblr.com/tagged/userstyles
> ✔  https://github.com/UserStyles
> 
> ***Getting in Touch***
> Stylish is a breathing, living product that is updating and growing all the time. If you have comments, suggestions, or have experienced any issues with Stylish, feel free to contact us at https://userstyles.org/contact. We’ll get back to you as soon as we can.
>  
> ***Support***
> You’ll find tutorials on how to use Stylish, including how to install styles (themes), create, and upload them to the Stylish library at https://userstyles.org/help. 
> 
> If you’ve encountered a broken theme, go to the theme’s page on the Stylish website and contact the style creator. The Stylish community is very responsive and eager to receive feedback. Don’t forget to give themes a thumbs up if you like them!
>  
> ✔  To build your own styles, check out instructions here: https://github.com/stylish-userstyles/stylish/wiki
> ✔  Important Note!
> 
> 
> We care very much about your privacy, so it is important to us that you understand our policy:
> For the purpose of providing you with the services offered by Stylish - showing you relevant and suggested styles for each web page you visit, as well as install count - we need to collect browsing data, as detailed in our privacy policy: https://userstyles.org/login/policy.
> 
> Version History:
> ✔  Version 1.6.2 - Changed UI; Added ‘Style Library’ to the extension
> ✔  Version 1.6.3 - Added ‘Installed Styles’ tab, including full style management functionality through ‘Installed Styles’ tab; Added Enable/Disable all styles toggle
> ✔  Version 1.7.0 (coming soon) - Fixing bugs; Enabling style install through extension
> 
> * Note that currently App and Global themes are not supported in the ‘Style Library’ tab. You can reach them through the Website Library:
> ★  Web Apps - https://userstyles.org/categories/app
> ★  Global Styles - https://userstyles.org/styles/browse/global
> 
> ### [Copy as Markdown - Chrome Web Store](https://chrome.google.com/webstore/detail/fkeaekngjflipcockcnpobkpbbfbhmdn '0.0')
> > 介绍: Copy as Markdown is a Chrome extension which can help you copy the following things as Markdown to your system clipboard:
> > 
> > - Current Tab as Link
> > - A Link on the Page
> >   - If the link has an Image in it, the copied Markdown will take that image as link text.
> > - An Image on the Page
> > - All Tabs as a List of Links
> > - Select Tabs for a List of Links
> > 
> > You can also customize keyboards shortcuts to copy link of tab(s) without a single mouse click.
> > 
> > Known Issues
> > 
> > - Cannot grab image.alt when copying image
> > - On Microsoft Windows, copied page link doesn't come with the link title
> > - (more issues in the issue tracker)
> > 
> > Source Code (MIT License)
> > 
> > https://github.com/chitsaou/copy-as-markdown
> > 
> ### [Biscuit for Chrome - Chrome Web Store](https://chrome.google.com/webstore/detail/flghkehjclghmdkeckchoolckhajedpl '0.0')
> 介绍: EVERNOTE DEVCUP 2013 BRONZE AWARD
> Biscuit has been featured in the App Store's "Best New Apps” for 30 different countries!
> 
> Biscuit for Chrome makes it super easy to look up English words, save wordlists, and review your vocab. Using our innovative UI/UX, read English content online more conveniently than ever before. Biscuit is the ultimate language learning tool. 
> 
> 
> [Functions Overview]
> 
> • Create your own word list in seconds with a few clicks of your mouse or by typing into our sidebar
> • Just hover your mouse cursor over a word to translate vocab and use study alerts to effortlessly review
> • Syncs across all your computers and mobile devices
> 
> 
> [Important Notes]
> - To use Biscuit for Chrome you must first install our Biscuit mobile app. Please go to your mobile app store and search for ‘Biscuit’ to download, and use the app to link your account to Chrome. 
> - You must use the same account as your Biscuit mobile app. If you have any issues, please email us at support@getbiscuit.com. 
> 
> 
> ### [Highlight to Search - Chrome Web Store](https://chrome.google.com/webstore/detail/floipahigmmkfhkoapmnijnlnboniglg '0.0')
> 介绍: Google Highlight to Search is a browser extension that helps you search keywords easily.
> 
> After you highlight keywords within a web page, you'll see magnifying-glass icon appear below the highlighted keywords.
> By either clicking on the icon or the keywords itself, search-box with Autocomplete enabled appears for you to search quickly and easily.
> 
> 
> By installing this extension, you agree to these terms:
> https://chrome.google.com/extensions/intl/en/gallery_tos.html
> This extension uses Google Search, and the data related to the query will
> be handled as described in Google's privacy policy:
> http://www.google.com/intl/en/privacypolicy.html
### [CaoLiu 1024 helper - Chrome Web Store](https://chrome.google.com/webstore/detail/fmcfkdaobigbkopahamahckjnifmmolc '0.0')
介绍: 本插件永久免费无广告，请尊重我的开发，有问题可到我的博客momane.com反馈，请不要随意打非5星评价，谢谢。
更新预告：
下一版本将增加一键下载帖子内图片的功能

1.1.5：
- 按住Ctrl再点击图片可以直接下载
- 自动关闭点击图片后打开的广告页面
- 一些种子页面可以自动下载种子，或者关闭掉页面的广告（主要用来修复有些下载页面广告遮盖下载按钮，导致无法下载）

1.0.4：
修复了一个乱码问题。增加了国产浏览器支持，其他主流国产浏览器安装方法见momane.com
1.0.0实现功能：
屏蔽广告
所有图片以及连接点击后直接打开, 无需再从草榴的广告页面跳转一次
屏蔽指定用户的帖子和回复

block ads
open all pics and link directly, no need redirect from caoliu ads page any more
block threads and comments of specific user

### [EditThisCookie - Chrome Web Store](https://chrome.google.com/webstore/detail/fngmhnnpilhplaeedifhccceomclgfbg '0.0')
> 介绍: The first and best cookie manager for Google Chrome.
> ★ Edit cookies
> ★ Delete cookies
> ★ Add a new cookie
> ★ Create cookies
> ★ Search cookies
> ★ Protect cookies (read-only cookies)
> ★ Block cookies (cookie filter)
> ★ Export cookies in JSON, Netscape cookie file (perfect for wget and curl), Perl::LPW
> ★ Import cookies in JSON
> ★ Limit the maximum expiration date of any cookie
> ★ Improve the performance, remove old cookies
> ★ Import cookies.txt
> ### [Mona New Tab - Chrome Web Store](https://chrome.google.com/webstore/detail/fohmiclpmoopioakgkokhbgcdphlonaj '0.0')
> 介绍: 快速搜索你访问过的网页历史记录;
> 快速搜索你杂乱无章的收藏夹;
> 比搜索引擎更智能，操作更简单;
> 清除关键字，轻敲ESC;
> 
> Quick search your visited web history;
> Quick search your desultorily favorites;
> More intelligent than the search engine, the operation more simple;
> Remove the key word, tapping the ESC;
### [Pricescout - Price Comparison & Coupons - Chrome Web Store](https://chrome.google.com/webstore/detail/gbkjddnnlgmahpnjjkiolhoophlpibfn '0.0')
介绍: Automatic Price Comparison & Coupon Notifications!

Pricescout automatically checks for lower prices and money-saving coupons while you shop, otherwise it stays hidden.
Once you've installed the free Pricescout browser extension on your browser (Chrome, Firefox or Safari), you just shop as you would normally, and Pricescout will help you save money through two primary features:

✔ Automatic Price Comparison:
When you are viewing a product in your web browser, Pricescout automatically scans over 21,000 stores for lower prices and will let you know who has the lowest price on the item you're viewing.  It's that easy.  You don't have to click anything and you no longer need to open a new tab and go to a price comparison site.

✔ Coupon Notifications
Are you tired of having to search Google every time you're looking for a coupon?  Pricescout's automatic coupon notifications will alert you to money-saving coupons without having to leave the site you're shopping.  All of Pricescout's coupons are reviewed by our editors which means you'll spend less time typing in expired codes and get the savings you want.

✔ Stays Hidden When You're Not Shopping
Unlike toolbars that take up valuable screen space when you're not using them, Pricescout is smart enough to know when you're shopping and will only discreetly appear when it's found coupons for the store you're viewing or price comparisons on the item you're viewing.

Think of the free Pricescout browser add-on as your personal shopping assistant that finds the lowest prices when you shop online. Shop with confidence knowing that you have found the best deal possible.

…………………………

How does it work?

Once you visit an online shop or a product-related web page, Pricescout gets active and analyzes the content of this page in the background, in order to read all relevant attributes of the offered product. If Pricescout finds better price or coupons it simply shows a light note right in your web browser. 

Depending on the availability of alternative offers and more information about a product may the duration of the search query vary. (between a few milliseconds to a few seconds).

Link to our simple Privacy Notice:
http://pricescout.io/privacy-notice.html

Any questions or feedback? Please drop us a note:
http://pricescout.io/contact.html


### [JSON Viewer - Chrome Web Store](https://chrome.google.com/webstore/detail/gbmdgpbipfallnflgajpaliibnhdgobh '0.0')
> 介绍: It is a Chrome extension for printing JSON and JSONP.
> 
> Notes:
> * This extension might crash with other JSON highlighters/formatters, you may need to disable them
> * To highlight local files and incognito tabs you have to manually enable these options on the extensions page
> * Sometimes when the plugin updates chrome leaves the old background process running and revokes some options, like the access to local files. When this happen just recheck the option that everything will work again
> * Works on local files (if you enable this in chrome://extensions)
> 
> Features
> * Syntax highlighting
> * 27 built-in themes
> * Collapsible nodes
> * Clickable URLs (optional)
> * URL does not matter (the content is analysed to determine if its a JSON or not)
> * Inspect your json typing "json" in the console
> * Hot word `json-viewer` into omnibox (type `json-viewer` + TAB and paste your JSON into omnibox, hit ENTER and it will be highlighted)
> * Toggle button to view the raw/highlighted version
> * Works with numbers bigger than Number.MAX_VALUE
> * Option to show line numbers
> * Option to customize your theme
> * Option to customize the tab size
> * Option to configure a max JSON size to highlight
> * Option to collapse nodes from second level + Button to unfold all collapsed nodes
> * Option to include a header with timestamp + url
> * Option to allow the edition of the loaded JSON
> * Option to sort json by keys
> * Option for C-style braces and arrays
> * Scratch pad, a new area which you can type/paste JSON and format indefinitely using a button or key shortcut. To access type `json-viewer` + `TAB` + `scratch pad` ENTER
> 
> This plugin is open source
> https://github.com/tulios
> 
> Bugs and suggestions
> https://github.com/tulios/json-viewer/issues
> 
> Contributors
> Thiago Pontes (@thiagopnts)
> @bluec0re
> @North101
> Ben Hollander (@benhollander)
> Mehdi Bahrami (@mehdibahraami)
> Reimund Trost (@reimund)
> Ben van Enckevort (@benvan)
> 
> License
> MIT License
> 
> Any questions tweet me @tulios
> ### [Wiki Search for GitHub - Chrome Web Store](https://chrome.google.com/webstore/detail/gdifdhnjmjaidbajhapmbcbnoocoeooc '0.0')
> 介绍: Search wiki of the repository on GitHub
### [Google Docs Offline - Chrome Web Store](https://chrome.google.com/webstore/detail/ghbmnnjooekpmoecnnnilnnbdlolhkhi '0.0')
> 介绍: The Google Docs extension makes it possible to edit your documents, spreadsheets and presentations when you aren’t connected to the Internet. Plus, you can copy and paste between Docs, Sheets and Slides.
> 
> To turn on offline access, visit https://support.google.com/drive/answer/2375012 
> 
> ### [Planetarium - Chrome Web Store](https://chrome.google.com/webstore/detail/gheikhdfflhlbemfmhcfpeblehemeklp '0.0')
> 介绍: Explore the stars and planets!
> 
> Planetarium shows you over 1,500 stars - that's every star up to magnitude "+5". These stars are the brightest in the night sky, the ones you can see with your own naked eye on a good dark night away from city lights.
> 
> HOW TO USE:
> Click and move your mouse to look around the sky. Click again to stop. Point at a star or planet to reveal its name, its constellation, its brightness (magnitude) and how far away it is in light years (LY) or astronomical units (AU). Also listed is the star or planet's Right Ascension (RA) and Declination (Dec) values - handy if you have a telescope!
> 
> You can also adjust the time and your viewing location to see the sky from any point around the world.
> 
> Use these shortcut keys to control the sky too:
> 
> Hide/show constellations – C
> Hide/show sky daylight – S
> Adjust year – Y or shift+Y
> Adjust month – M or shift+M
> Adjust day – D or shift+D
> Adjust hour  – H or shift+H
> Adjust minute  – N or shift+N
> Adjust latitude – L or shift+L
> Adjust longitude – K or shift+K
> 
> Also, use the arrow keys ←↑↓→ on the keyboard to move around the sky. Press the F key to go full-screen.
> 
> Happy star gazing!
> ### [Extension Automation - Chrome Web Store](https://chrome.google.com/webstore/detail/ghopjgdkodchjclkkfdekhjfomdbakkb '0.0')
> 介绍: Extension Automation makes it easier to manage other extensions by automatically enabling or disabling them based on the webpages you visit. This extension helps reduce the visual clutter of other extensions and keeps them from running unnecessarily in the background. 
> 
> New features:
> 
> -You can now choose to enable OR disable an extension on certain pages.
> -Extension Automation now keeps track of all your open tabs.
> -Speed and performance improvements.
> -Interface improvements.
> 
> 
> How to use Extension Automation:
> 
> - Install the extension
> - Click on the new button at the top of your browser, from here you can quickly add new website addresses or keywords to monitor.
> - Extension Automation will automatically activate the chosen extensions for the specified keywords.
> - Click on "View Settings" in the popup menu to see your current entries and tweak them.
> 
> Changelog:
> v.1.1.3: added import/export functionality (via copy and paste); fixed info sometimes being submitted twice. 
> 
> (If you have any difficulties, encounter bugs, or have feature requests, please go to chrome webstore details page and click "support". I'll help you out as soon as I can.)

### [Inbox by Gmail - Chrome Web Store](https://chrome.google.com/webstore/detail/gkljgfmjocfalijkgoogmfffkhmkbgol '0.0')
> 介绍: By installing this item, you agree to the Google Terms of Service and Privacy Policy at https://www.google.com/intl/en/policies/.

### [Reddit New Tab - Chrome Web Store](https://chrome.google.com/webstore/detail/gkobcdoenbilkdahndhmcdjbofoldfcd '0.0')
> 介绍: Top Posts for the past 24 hours from the Sub Reddits you have subscribed are taken. You can choose the subreddits by entering their url on the options page. See the screenshots for more information
> 
> Changelog:
> 
> * v2.3.4: Fix bug where the last category was never selected
> * v2.3.3: Remove scroll bar on options page
> * v2.3.2: Now you can click on the content to open the link
> * v2.3.1 : Fixed bug that caused previous button to keep showing on refreshing
> 
> Author: 
>     Ankit Sultana

### [OneNote Web Clipper - Chrome Web Store](https://chrome.google.com/webstore/detail/gojbdfnpnhogfdgjbigejoaolejmgdhk '0.0')
> 介绍: You're busy. OneNote Web Clipper lets you quickly clip all or part of a web page to OneNote, and save it for later. Clip images, pdfs, videos, or a visual bookmark of a page. Best of all, you can access them from any computer, tablet, or phone - even when you're offline.
>  
> CLIP YOUR WAY
>  - NO CLUTTER! Articles, recipes, or products can be clipped without all the ads, navigation, and noise.
>  - Highlight text, adjust the fonts, or add a note before you clip.
>  - Clip the whole page or several selections on the page. It's up to you.
>  
> WHAT TO CLIP
>  - All or part of a web page
>  - PDF files - online or on your computer
>  - Any image on a web page
>  - Videos from YouTube or Vimeo
>  - Create a visual bookmark of the page 
>  
> GREAT FOR
>  - Travel
>  - Business
>  - Shopping
>  - Recipes
>  - Research
>  - News
>  - Inspiration
>  
> TAKE IT WITH YOU 
>  - Anything you clip to OneNote will be available on all your devices, even if you're offline.
>  - Use OneNote's powerful search to find your information on any device.
>  - Share your information with others.
> 

### [Holmes - Chrome Web Store](https://chrome.google.com/webstore/detail/gokficnebmomagijbakglkcmhdbchbhn '0.0')
> 介绍: Got bunch of bookmarks in Chrome? Never find the bookmark you're looking for?
> 
> Holmes is here to search for your bookmarks!
> 
> Omnibox integration is back!
> You users missed Watson so bad so we thought to bring him back! And he is faster than ever!
> 
> As always, you find him from url bar. Just type * and press tab and you're ready to search!
> 
> Holmes also activates by keyboard shortcut! Press Alt+Shift+H and you're ready to go! You can always change the shortcut for your liking. Go to Chrome Menu > Tools > Extensions. Scroll down to bottom, press "Keyboard shortcuts" link and add custom shortcut to Holmes!
> 
> ** NEW in version 3 **
> 
> * Completely rewritten search engine
> * Shortcut Alt+Shift+H added!
> * 10 results are shown
> * No settings
> * Bookmarklets are removed by default
> * Much cleaner, hassle free look
> 
> ** Version info **
> v.3.3.0
> 
> * Holmes now autofocus input field by default
> 
> v.3.2.1
> 
> * "NEW" label bug fixed
> 
> 
> v.3.2
> 
> * Fuzzy search implemented both Holmes and Watson - big thanks to krisk's Fuse library -> https://github.com/krisk/Fuse
> 
> v.3.1.7
> 
> * Fixed omnibox bug when only one result opens bookmark in Google search
> * Fixed Holmes input autofocus
> 
> v.3.1.6
> 
> * Holmes website link added to extension
> 
> v.3.1.5
> 
> * Default shortcut wasn't working! Now it does!
> * Added guide to change default shortcut. See top of this text for more info.
> 
> v.3.1.4
> 
> * When bookmark was added or removed Holmes didn't recognize the changes. Now fixed.
> 
> v.3.1.3
> 
> * Minor bug tackled
> 
> v.3.1
> 
> * Omnibox integration rewrited from ground up!
> 
> v.3.0
> 
> * Completely rewritten search engine
> * Shortcut Alt+Shift+H added!
> * Only 10 results are shown
> * No settings
> * Bookmarklets are removed by default
> * No omnibox integration anymore
> * Much cleaner, hassle free look
> 
> 
> v.2.2.2
> 
> *Blog link removed from the start.
> 
> v.2.2.1
> 
> *FIXED a bug from clicking bullet page navigation. Now it works properly.
> 
> v.2.2
> 
> Welcome message changed.
> 
> v.2.1.1
> 
> Compatibility update for the upcoming browser versions
> 
> v.2.1
> 
> *NEW Showing info when Holmes is upgraded to higher version
> *NEW Logo updated...again :)
> * Minor UI changes.
> 
> v.2.0
> 
> *NEW - Watson, the Omnibox search integration
>    - Type asterisk(*) and press tab in url bar
> *NEW - Logo typography change
> 
> v.1.2
> 
> * NEW - Added keyword "new:".
> * Smallest icon redesign
> * Minor fixes.
> 
> v. 1.1
> 
> * NEW - Options added. Toggle from seach field right corner.
> * Remove bookmarklets from search (bookmarks that starts with 'javascript:').
> * Save last state. Continue from last point.
> 
> * UI improvements. Maven Pro from Google Fonts are loaded as main font.
> * Matched search string is higlighted in results as red.
> * History search is depracated. Chrome has so nice history search so this is not a needed feature. Let's focus on bookmarks!
> 
> 
> v.1.0.1
> * Ctrl+D is deprecated. Preventing Windows users to create bookmark by pressing the combination.
> 
> v.1.0
> * Initial release

### [Pinterest Save Button - Chrome Web Store](https://chrome.google.com/webstore/detail/gpdjojdkbbmdfjfahjcgigfpmkopogic '0.0')
> 介绍: The Pinterest Save button lets you save any idea you find around the web so you can easily get back to it later. 
> 
> Just click to save dinner recipes, style inspiration, home projects and other ideas you want to try. 
> 
> The Pinterest Save button also has built-in visual discovery technology—hover over any image and click the visual search tool to instantly discover visually similar ideas on Pinterest.
> 

### [Markdown Reader - Chrome Web Store](https://chrome.google.com/webstore/detail/gpoigdifkoadgajcincpilkjmejcaanc '0.0')
> 介绍: MarkdownReader:
> 
> markdownReader is a extention for chrome, used for reading markdown file.
> 
> Features:
> 
> 1. Reading markdown file
> 2. Auto reload local file when file is changed
> 3. Highlight the code area
> 4. Show outline beside the content
> 5. Support extension: Tasklist, table, LaTeX
> 6. Toggle raw mode and markdown mode by double Click
> 
> Install
> 
> 1. Install plugin: https://chrome.google.com/webstore/detail/markdown-reader/gpoigdifkoadgajcincpilkjmejcaanc
> 2. Open plugin center: chrome://extensions/, check "Allow access to file URLs"
> 3. Drag md file to chrome
> 
> 
> Source code:
> 
> https://github.com/yaniswang/markdownReader
> 
> License:
> 
> markdownReader is released under the MIT license:
> 
> The MIT License
> 
> Copyright (c) 2014 - 2017 < yanis.wang@gmail.com >
> 
> Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:
> 
> The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.
> 
> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

### [Wappalyzer - Chrome Web Store](https://chrome.google.com/webstore/detail/gppongmhjkpfnbhagpmjfkannfbllamg '0.0')
> 介绍: Wappalyzer is a cross-platform utility that uncovers the technologies used on websites. It detects content management systems, ecommerce platforms, web frameworks, server software, analytics tools and many more.

### [Color Tab - Chrome Web Store](https://chrome.google.com/webstore/detail/hchlgfaicmddilenlflajnmomalehbom '0.0')
> 介绍: Color Tab fills up your "new tab" screen with a refreshing color palette from the best of Color Hunt's palettes. Each time you open up a new tab, the page will be replaced by a random beautiful color scheme.

### [Toby for Chrome - Chrome Web Store](https://chrome.google.com/webstore/detail/hddnkoipeenegfoeaoibdmnaalmgkpip '0.0')
> 介绍: “I don’t want to have 3,000 tabs open anymore” – from a new Toby user
>  
> Bookmarks are for books, not browsers. Organize your browser tabs into Toby so you can access key resources in one-click instead of seven.
>  
> Toby is better than bookmarks, it levels up your Chrome browser. Toby is a visual workspace that lives on every new tab. Add new tabs by dragging and dropping your browser tabs into collections or save a whole session in just one-click. Access all of your collections on any desktop with automatic sync. Use tags to organize your collections or create notes for your to-dos.
>  
> Toby is changing the way you save and access tabs by making it easy and fun to use.  
>  
> ➤ #1 Chrome extension of 2016 from Product Hunt
> ➤ Google Chrome’s Best of 2016 list
> ➤ Featured in MIT Tech Review, Business Insider, Brit + Co and 30 other publications
> ➤ Teams who work at Bazaarvoice, Twitter, New Relic, IBM, and more are using it daily
> ➤ Over 9,250 love letters written by #TobyFriends in over 144 countries around the world
> 
> WHY TAB MANAGEMENT?
> 
> We built Toby to provide distraction-free focus, saving you time spent switching between tabs from web apps and websites. A survey of Toby customers showed that Toby saves up to 8 hours per week, per person—the equivalent of ~48 work days per year.
>  
> ★ Pause and resume work
>  
> Feel like your workflow is bottle-necked by context switching? With one-click Toby is able to save your browser session, or open it when you’re ready to resume your task.
>  
> ★ Clear the clutter
>  
> Using different browser windows to separate tabs into to-dos, dashboards, and spreadsheets is not ideal. With Toby, you can remove the clutter by using one window with the tabs you need, right when you need it.
>  
> ★ Be an expert everywhere you work
> 
> Get instant access to the tabs you need to get the job done. Toby is able to search for any website inside of any collection, letting you find exactly what you’re looking for in seconds.
>  
> ★ Flexible with your work habits
>  
> Toby lives on every new tab and lets you speed dial into the websites or apps you use on a daily basis. Quick and consistent access is the key to Toby’s value.
>  
> ★ Stop emailing yourself links
>  
> Access Toby on any page just by right-clicking. Now you can spend more time doing work while queuing up all of your favorite articles to read later.
>  
> GIVE US A 5-STAR REVIEW
> ★★★★★
> Genuinely enjoy the Toby experience? Helped you save time at work? Support the Toby community by giving us a great review!
>  
> GET IN TOUCH
> Twitter: @TobyForTabs
> Contact: hello@gettoby.com
>  
> SUPPORT & BUG REPORTING
> http://www.gettoby.com/contact
> 
> PRIVACY AND PERMISSIONS
> http://www.gettoby.com/privacy
> 

### [享阅 - Chrome Web Store](https://chrome.google.com/webstore/detail/hdfnknjhidkbfmcjknjejamfkpgdkihf '0.0')
> 介绍: 自动识别浏览器中你感兴趣的内容，将其推送到kindle或者其他设备，你还可以自己通过鼠标选择内容来进行推送，完全免费
> 
> 扩展特性及使用方法参见： http://enjoyread.cn
> 
> Bug，意见等 smallbanglouis@gmail.com

### [LastPass: Free Password Manager - Chrome Web Store](https://chrome.google.com/webstore/detail/hdokiejnpimakedhajhdlcegeplioahd '0.0')
> 介绍: Only remember one password - your LastPass master password. Save all your usernames and passwords to LastPass, and it will autologin to your sites and sync your passwords everywhere you need them.
> 
> "This robust password manager is a must-use free tool that supports multiple operating systems and browsers." - PCMag Editors' Choice
> 
> Save Everything:
> - Store login usernames and passwords
> - Checkout fast by adding credit cards & shopping profiles
> - Attach docs, PDFs, images, audio, and more
> - Save any piece of data you need to keep secure and easy-to-find 
> - Manage everything from a simple, searchable vault
> - Add, edit, view, delete, and organize your passwords
> 
> Access Everywhere:
> - LastPass is free to use on any computer, laptop, phone or tablet
> - Install the LastPass browser extension on all computers
> - Login with the same LastPass account everywhere
> - Anything you save on one device is instantly available on all your other devices
> - Download LastPass to all your computers and get our app for your smartphone or tablet
> 
> Improve Your Online Security:
> - Generate secure passwords to replace weak ones
> - Create new passwords as you sign up for sites
> - Protect your LastPass account with multifactor authentication
> - Use the LastPass security check to review your passwords and flag weak and duplicate passwords
> 
> Simplify your life:
> - Never forget another password
> - Generate strong passwords that you don't have to remember 
> - Passwords are autofilled for you as you go to your sites - less typing! 
> - Securely share your passwords with friends and family 
> - Only worry about one master password
> 
> Only you know your master password, and only you can access your vault. Your master password is never shared with LastPass. That’s why millions of people and businesses trust LastPass to keep their information safe. We protect your data at every step.
> 
> Learn about more features and get LastPass Password Manager for Internet Explorer, Firefox, Safari, and Opera from www.LastPass.com

### [IE Tab - Chrome Web Store](https://chrome.google.com/webstore/detail/hehijbfgiekmjfkfjpbkbammjbdenadd '0.0')
> 介绍: .
> Top 10 Chrome extension since 2009!
> 
> -- WINDOWS ONLY -- WINDOWS ONLY --
> 
> IE Tab exactly emulates IE by using the IE rendering engine directly within Chrome.  This will enable you to use ActiveX controls and test your web pages with different versions of IE (IE6, IE7, IE8, or IE9).
> 
> -- FEATURES --
> 
> * Create a list of URLs that will automatically open in IE Tab
> 
> * Group Policy support for enterprise deployments
> 
> * Securely use the old IE rendering engine
> 
> * Edit Sharepoint documents instead of opening read-only
> 
> * Use Java, Silverlight, and ActiveX in Chrome seamlessly
> 
> 
> 
> 
> FREQUENTLY ASKED QUESTIONS
> 
> 1. Why do I have to install ietabhelper.exe?
> 
> IE Tab uses the Internet Explorer rendering engine. This rendering engine can't be directly accessed from a Chrome extension, so we need a helper process to talk between the Chrome extension and the rendering engine. 
> 
> 2. Did IE Tab always require this extra program?
> 
> No. Chrome used to support a technology called NPAPI (the Netscape Plugin API) which allowed extensions to access local computer resources. IE Tab used to use that functionality to access the Internet Explorer rendering engine. But Chrome removed NPAPI support, so we were forced to implement a new solution, and that solution requires a separate helper executable. From a technical standpoint, the only real change is that our code moved from an NPAPI .DLL file to a helper .EXE file. 
> 
> 3. Is the IE Tab Helper application safe?
> 
> Absolutely! IE Tab has always used native code, and we have always treated the security of our 2+ million users very seriously. So you can rest assured that this helper executable is secure and trustworthy. 
> 
> 4. I'm an enterprise customer, how do I deploy the IE Tab Helper automatically?
> 
> We have enterprise deployment options, please contact us at support@ietab.net for details. 
> 
> 
> The Privacy Policy for the IE Tab extension can be found here:  http://www.ietab.net/privacy.html
> 
> 

### [Additor - The Simplest Bookmark & Highlighter - Chrome Web Store](https://chrome.google.com/webstore/detail/hfllajanfnlimffhkjbondolipoimcgn '0.0')
> 介绍: Featured on Product Hunt and Chrome Web Store 🙀 🙀
> 
> Additor for Chrome is the most minimal and functional bookmark and highlighter.
> From Youtube to PDF, you can easily save, organize, and share contents.
> 
> For marketer, designer, researcher, blogger, student, and etc, it's time to do more with less.
> Additor also support powerful collaboration with your own visual knowledge library.  
> 
> Updates
> - Undo option
> - Shortcuts
> - Keyboard UX

### [Papier - Chrome Web Store](https://chrome.google.com/webstore/detail/hhjeaokafplhjoogdemakihhdhffacia '0.0')
> 介绍: Got something on your mind?
> 
> Did you know that the average person has about 60,000 thoughts a day? And that we spend about 7 hours looking at screens? Now with the Papier extension for Chrome, just open a new tab and trap your best thoughts. They'll be backed up directly to Chrome: no accounts, no syncing. 
> 
> Simple, clean, and distraction-free, Papier declutters your thoughts so you can focus on the content. Let nothing get in the way of your notes.
> 
> Made with 💚 by Muxu.Muxu

### [Random Quote - Chrome Web Store](https://chrome.google.com/webstore/detail/hhompecpighdhclapocgaaadjnmgahoi '0.0')
> 介绍: Instantly see a random quote with a colored background when you open a new tab.
> 
> Features:
> - Awesome quotes
> - Open a new tab, see a quote instantly
> - Non intrusive, won't bug you

### [Tamper Chrome (extension) - Chrome Web Store](https://chrome.google.com/webstore/detail/hifhgpdkfodlpnlmlnmhchnkepplebkb '0.0')
> 介绍: To use it, refresh the website and look at the developer tools (left-click -> inspect element). Tamper Chrome will appear in a new tab. See the tutorial here: https://github.com/google/tamperchrome/blob/master/README.md
> 
> Tamper Chrome allows you to monitor requests sent by your browser and the responses. You can also modify requests as they go out, and to a limited extent modify the responses (headers, css, javascript or XMLHttpRequest responseText).
> 
> See what websites are sending in the background, modify submissions, switch out scripts, alter AJAX responses, Tamper Chrome puts the power of your browser back in your hands.
> 
> Tamper Chrome will prompt you to install its companion application when you first run it.
> 
> If you need help go to:
> https://groups.google.com/forum/#!forum/tamper-chrome-help

### [copy 2 clipboard with ease - Chrome Web Store](https://chrome.google.com/webstore/detail/hiiobhaaokpmdmkkcaokdlanlemmcoah '0.0')
> 介绍: A simple and quick way to copy title and url with ease in chrome browser.
> 
> features
> 
> There have four options:
> 
> -	copy title only
> -	copy title and url
> -	copy title and shorten url
> -	copy url only
> -	copy shorten url only
> 
> Copy title, url pattern:
> 
> the default copy patter is **url (title)**, you can change whatever you want but keep **url** and **title** keyword.
> 
> Shortcut
> 
> you quick launch `copy 2 clipboard with ease` one feature by custom keyboard shortcut.
> 
> Change log
> 1.0.3 / 2016-11-06
> 
>   * modify permissions
> 
> 1.0.2 / 2015-11-23
> 
>   * fix shorten API error.
> 
> 1.0.1 / 2015-04-05
> 
>   * pattern input problem and other bug fixed.
> 
> 1.0.0 / 2015-04-03
> 
>   * add options settings sync via Google account between different chrome browser. Change UI themes from Bootstrap to semantic-ui. minors bug fixed.
> 
> 0.0.110
> 
>  * add copy link with name feature.
> 
> 0.0.109
>   * chrome shortcut support. Default extension is "Shift+Alt+C". You can setup shortcut you want to enable fast copy one option of 5.
> 
> 0.0.104

### [G.lux - Chrome Web Store](https://chrome.google.com/webstore/detail/hinolicfmhnjadpggledmhnffommefaf '0.0')
> 介绍: G.lux is a Chrome Extension which changes the color temperature of the browser tab. An f.lux alternative for ChromeOS and Chrome Browser users.
> 
> G.lux is a free and unofficial variation of f.lux, a desktop app that automatically changes the color temperature of your monitor as the sun goes down. Monitors are typically daylight balanced, which can interfere with your sleep cycle when using them after sunset. G.lux is an alternative for those who are unable to install f.lux due to their operating system or administrator access settings, such as schools and workplaces. In addition, G.lux is currently the only f.lux alternative for millions of ChromeOS users worldwide.
> 
> Why would I want to change the color temperature of my webpages?
> Modern displays are 'daylight balanced' causing your brain to think it's daytime, which can keep you from falling asleep at night. In the evening, our eyes naturally expect a more orangish 'tungsten balance.' G.lux is also a useful companion for multitasking photo editors, movie watchers and anyone looking to dim solely their browser without the rest of their desktop applications.
> 
> Features:
> -Change the color temperature of your browser/websites.
> 
> -Make your websites darker without using the monitor or operating system display settings.
> 
> -Choose a custom color for your webpages. You can even make your screen pink or green!
> 
> -Variable filter intensity: One-extension for all screens and brightnesses!
> 
> -Color and intensity settings are saved across multiple Chrome browsers or ChromeOS devices.
> 
> January 25, 2017 version 3.1 Changelog:
> -Colors can now be saved on a per website (domain) basis, which overrides the default color.
> -Color is now applied right away when saved, no page refreshing required!
> -Selected colors are previewed in realtime on the visible tab.
> -Improved the injection of the overlay div (but due to a limitation in Chrome we still can't color the white shown between new webpages loading).
> -Fixed an issue with times between midnight-0100.
> 
> June 18, 2014 version 3.0 Changelog:
> -New in 3.0! (Most popular user suggestion) Select a time of day to activate automatically! Set the activation time to your local sunset for an optimal circadian rhythm!
> 
> Tips:
> -Use G.lux with the black setting and a low filter intensity to create a dimmed screen between the 'screen off' position and the lowest brightness settings on your monitor. Sometimes the lowest setting just isn't dim enough!
> 
> -Select a dark theme for Chrome. This extension only changes the color temperature of the page(s) you’re viewing and not the omnibar/tabs at the top of the browser. Alternatively, you may wish to use Chrome in Full-screen mode (F11).
> 
> Notes and known issues:
> -The color change only comes into effect when the page has been fully loaded. There does not appear to be a solution to this behavior in Chrome at this time.
> 
> Permissions:
> -Access to all websites is required, because the Chrome Extension needs to be able to modify each website to inject a filter over top of what you're viewing. This Chrome extension does not collect personal information or browsing history in any way. As an open source piece of software, the community is welcome to inspect the source of chrome extensions for malicious intent and even submit a pull request at https://github.com/IntegersOfK/G.lux

### [SuperSorter - Chrome Web Store](https://chrome.google.com/webstore/detail/hjebfgojnlefhdgmomncgjglmdckngij '0.0')
> 介绍: Are your Chrome bookmarks a mess? SuperSorter can help!
> 
> With one click of its button, SuperSorter sorts all of your bookmarks, in all your folders, into alphabetical order. It sorts folders too and if you like it will put the folders at the top of the list above the bookmarks (like in most other browsers).
> 
> SuperSorter also deletes empty bookmark folders, deletes duplicate bookmarks in the same folder and merges neighbouring folders with the same name. SuperSorter can also sort bookmarks automatically every few minutes, making it even easier to keep everything tidy.
> 
> Beware: there is no undo function. Use at your own risk!
> 
> HOW TO REPORT BUGS:
> 
> If you find a bug please follow the "extension support" link to the SuperSorter discussion group and post a description of the problem there. I may need to ask you some questions before I can figure out why it doesn't work for you.
> 
> RELEASE NOTES:
> 
> Version 0.4.0 introduces a new feature: the "Find all duplicates now" button displays a list of all your duplicate bookmarks, so you can choose which ones to delete. 
> 
> Version 0.4.1 fixes a bug in which the sort order for the list of duplicates could be inconsistent.
> 
> Version 0.4.2 adds (by popular demand) an option to ignore the Bookmarks Bar during all operations. This is now the default setting (that is, the Bookmarks Bar will be ignored unless you choose otherwise).
> 
> Version 0.4.3 is a minor bugfix release.
> 
> Version 0.4.4 is a maintenance release switching to the new manifest v2.0 format.

### [DuckieTV - 'New Tab' mode - Chrome Web Store](https://chrome.google.com/webstore/detail/hkbamkappmgfjjahmnlngibomenmbbdf '0.0')
> 介绍: DuckieTV is a Google Chrome / Opera extension that takes care of TV-Show addicts by providing a personalized TV-Show calendar. DuckieTV makes sure the information is always up-to-date and gives you an integrated blocking-resistant torrent search to help you get to the right download as easy as possible.
> 
> With the integrated DuckieTorrent client you can connect DuckieTV to your local uTorrent/BitTorrent client and be updated on the download progress without switching applications. Experimental ChromeCast integration even provides the possibility to stream videos to your TV while still downloading.
> 
> As of v0.60 DuckieTV also is also finally becoming a worthy SickBeard competitor by introducing an automatic downloading of shows that have aired and translations into 11 languages. (English, Deutch, Español, Français, Italiano, 日本, 한국어, Nederlands, Purtugese, Русский, Svenska, 简体中文 )
> 
> !!! If you're looking for the version that doesn't take over your 'new tab' page look here !!
> 
> https://chrome.google.com/webstore/detail/cdfkaloficjmdjbgmckaddgfcghgidei/
> 

Changelog: 
* v1.1.4 : Fixed images. Swapped out a lot of search engines. Many, many bugfixes and new features. Check the changelog at https://github.com/SchizoDuckie/DuckieTV/releases/tag/1.1.4
* v1.1.3 : Updated translations, many bugfixes and new features. check the changelog at https://github.com/SchizoDuckie/DuckieTV/releases/tag/1.1.3
* v1.1.2 : Fixed missing deps in previous release.
* v1.1 : Changelog is too long to list here. Please check it at http://duckie.tv/ !
* v1.00 : Completely revamped user interface (now with 100% more sexyness) - Added support for Tixati, Transmission and qBittorrent torrent clients - Added Strike and RarBG torrent search providers - Added calendar grouping for netflix episode dumps - Initial version of Subtitle search available from episodes panel - Removed Chromecast integration. (Use getvideostream.com and the app!) - Autodownloads now use the configured torrent provider - Revamped the way torrent search engines are created and registered - Shows can be marked as downloaded as well as watched, and downloaded episodes can be highlighted on the calendar - Added Trakt.TV Trending category filters, caching for Trakt.TV trending list - Fixes for DuckieTV standalone: now using frame-less window, open external links in default browser, window and unminimize from tray works in Ubuntu, added upgrade check and notification, and zoom control is now 1:1 with chrome browser - Database performance improvement (including less frequent ratings updates) - added 'Watch on Netflix' button for Netflix shows - numerous other small changes and bugfixes to list 
* v0.94 : Switched to the new (hopefully more stable) trakt.tv endpoint, Added actor and rating info back to serie details, Fixed KAT Mirror Resolver and custom setting and added back TPB mirror selection to torrent settings, Changed default KAT mirror back to kickass.to, Minor tweaks to auto-download and updatecheck mechanisms, Built a little standalone website to turn off uTorrent's ads with one click. ( http://schizoduckie.github.io/PimpMyuTorrent/)
* v0.93 : Welcome back TPB! Added ShowRSS.info as a custom datasource
* v0.92 : Fixed problem with deployment script: moment.js was not included, breaking torrent searches for shows that are released with a date format.
* v0.91 : Fixed some people's problems with the upgrade and now-missing watched indicators (They'll restore automatically).Removed Torrents.fm (domain cancelled), Fixed OldPirateBay on https. Fixed Timezone offset for torrent search with dates, added some requested scene names and updated some translations in Italian, Dutch and English.
* v0.90 : Fixed TraktTV v2 API, compensated for TPB being down, many performance improvements, updated dutch and italian translations
* v0.82 : Fixed chrome v39 compatibility, sync engine still a work in progress.
* v0.81 : Some changes to the add to favorites screen, now showing detailed show information on hover. Also, some changes to make DuckieTV work in standalone mode, no chrome required! Get it at https://github.com/SchizoDuckie/DuckieTV/releases/
* v0.80 : A minor update with big impact: Daylight Savings Time fix by /u/garfield69
* v0.79 : Fixed infinite digest in calendar preventing usage on huge databases. Updated torrent autoDownloader to handle the same logic as the torrentDialog
* v0.78 : Fixed 'yes-all' and 'no-all' dialogs..
* v0.77 : Added 'yes-all' and 'no-all' buttons for confirming remote deletions in storage sync, preventing users to potentially have to confirm loads of deletions. Fixed StorageSyncService only syncing one show at a time.
* v0.76 : fixed a potential problem with hidden shows on the calendar and missing cast_sender.js
* v0.75 : DuckieTV is much faster now, Easily delete shows from series you're watching, Database write indicators, Improved error handling and credentials validation for Trakt.TV, Update mechanism improved to handle TheTVDB reassigning ID's (fixing duplicate/disappearing shows on your calendar after an update), IMDB / Wikipedia links on the show details page, Added ability to hide 'Specials' for shows (like Dr. Who), Bandwidth consumption improvements, Shows that have ended will now only be checked for updates every 2 weeks, Fixed Torrent Dialog search box to automatically grab keyboard focus, Torrent auto-download service now runs every 2 hours instead of every 4 hours, Fixed 'Scenename' lookup for downloads.
* v0.70 : One of the most requested features was added: You can now sync your shows and watched episodes from and to Trakt.TV! The "Most visited sites" drawer can now be changed to open on click, syncing your favorite shows via your Google account works again. and you can now print the calendar.
* v0.62 : Fixed a problem with the add series typeahead
* v0.61 : Fixed deployment problem for english/uk users.
* v0.60 : New tabs interface in settings thanks to /u/Js41637, Introduced Internationalisation and translations thanks to /u/Garfield69, Initial translations into English and Dutch, the 9 other most popular languages are included in auto-translated form. Optimized watched indicator in calendar, added Trakt.TV's trending shows to 'series you're watching', made it possible to use the basic features of DuckieTV as a regular website: http://DuckieTV.github.io/DuckieTV/ (browsers that support WebSQL only! Tested on Chrome/Opera/Android)
* v0.55 : Fixes and improvements for the calendar, double loading images and GUI by /u/Garfield69 and /u/Js41637 Thanks guys!!!
* v0.54 : Layout CSS tuning and bugfixes by /u/Js41637 (Thanks!). Support for uTorrent 3.4.1 alpha, Fixed KAT parsing, Added extra permission for huge series (>5mb) databases.
* v0.53 : CSS/layout fixes, Fixed the timers that went missing, fixed the auto-update service, fixed restore watchlist timers, improved memory usage on backup restore.
* v0.52 : Fixed magnet URI catching and saving everywhere you can launch a torrent search for an episode. Added a popup menu on the torrent dialog with access to source, torrent and magnet links for each result
* v0.51 : Fixed several marking episode as watched issues
* v0.50 : Complete UI overhaul, uTorrent integration, experimental Chromecast integration, many performance improvements
* v0.43 : Made sure migrations don't run on fresh installs
* v0.42 : Fixed missing scheduled event and chrome alarm delete procedure when deleting series.
* v0.41 : Fixed 'browser action mode' not launching on icon click.
* v0.40 : Switched to Trakt.TV API. Created backup/restore function. Added seasons. Reworked torrent dialog. Fixed timezone mess. Added Calendar week mode. temporarily disabled browser sync. Added 'download whole season'. Added 'download .torrent' link in dialog.
* v0.35 : Synchronized versions after another manual screwup, created fully automated deployment process using macro's. Fixed 10/10 ratings in overview.
* v0.33 : Updated sync option with permanent sync feature. Added functionality for when remote series are deleted. Multiple styling and consistency updates. Synced date formats. Added episode ratings chart on series overview page.
* v0.32 : Added experimental Sync option. Hit the 'sync' button in settings to push your current series list into the cloud. Open DuckieTV on another computer computer (signed in with the same google account), sit back and watch the magic. (watched episodes will be transferred in a later version)
* v0.31 : Fixed grid layout for 1200+px wide screens, Fixed naive TVRage id resolving for something more solid. Now matches both by name and optionally firstaired on multiple matches.
* v0.30  :  Renamed from 'SeriesGuide Chrome v2' to DuckieTV! Reworked TVRage parsing to resolve bugs with episode numbering. Special handling for pawn stars like renaming errors means that these have less info to show for now, but more works properly. Implemented adding missing episodes from TVRage (like S01E01 that's missing for a lot of shows).
* v0.28 : Fixed layout bugs, timezone offset for the other half of the world, default settings
* v0.27 : Implemented quality selection for episode search queries in settings. You can now search by default for none/HDTV/480p/720p/1080p
* v0.26 : Fixed a timezone offset bug for historical dates, showing shows that have already aired at the wrong date.
* v0.25 : GUI updates: Made backgrounds blend with black to improve readability, Implemented new settings toggles: 'extra wide calendar' and 'hide torrent searchbox from main page', created switch to show your favorite shows in grid mode (which takes less space), various touchups. 
* v0.24 : Implemented switch preference to select default search provider (ThePirateBay or KickassTorrents) that's used for downloads by default, fixed setting custom tpb proxy gui
v0.23 : Fixed a problem with my deployment script, switching the 'browser action mode' for 'new tab' mode. Sorry for that :(
v0.22 : Fixed a parsing problem for TPB results.
v0.21 : Added setting to disable torrent functionality, Added piratebay mirror resolver and manual override, added setting to hide TopSites, switched to google's site screenshot service like used on their new tab (the api that I used was getting slow due to the popularity of this extension) merged to a single codebase for both extensions.
v0.20 : Implemented Scene Name Resolver for series that have an alternate scene name 
v0.19 : Implemented automagic PirateBay Proxy Resolver
v0.18 : Fixed date bug showing items on previous day on calendar.
v0.17 : Styling improvements, layouting and useability improvements. created #/watchlist url (still hidden for now), torrentfreak top10, mocked up #/settings page
v0.16 : Fixed TVRage sync and made it automagic
v0.15 : Cleaned up the layout and merged search engines. 
v0.14 : TVRage Sync under series details. Fixes wrong episode numbers in the TVDB database for shows like 'Pawn Stars'. (Github #20) Click the Episode number column in the table to activate.
v0.13 : Browser Action Mode created
v0.12 : Added kickass torrent search for when thepiratebay is down. Will be reworked into something nicer soon
v0.11 : First 'browser action' release
v0.10 : First public release.


Permissions explanation:
- Read and modify browser history -> For the access to the ChromeTopSites api (to show your most used tabs)
- Access to your data on all websites -> For being able to scrape several sites.

If you want to verify what's happening in code yourself, check the github repo:

https://github.com/SchizoDuckie/seriesguide-chrome/tree/angular/
### [一叶书签 - Chrome Web Store](https://chrome.google.com/webstore/detail/hlahagafhhglgfefflokbaidlneedghl '0.0')
> 介绍: 一叶书签，书签便捷小工具

### [JetBrains IDE Support - Chrome Web Store](https://chrome.google.com/webstore/detail/hmhgeddbohgjknpmjagkdomcpobmllji '0.0')
> 介绍: With the JetBrains IDE Support extension for Google Chrome you can debug JavaScript code in Chrome from WebStorm, PhpStorm, IntelliJ IDEA Ultimate, PyCharm Professional, and RubyMine. In addition to that, you can see the changes you make in HTML or CSS files in the browser right away, without reloading the page, thanks to the Live Edit plugin.

### [Google Keep - notes and lists - Chrome Web Store](https://chrome.google.com/webstore/detail/hmjkmjkepdijhoojdojkdfohbdgmmhki '0.0')
> 介绍: Quickly capture what's on your mind and share those thoughts with friends and family. Speak a voice memo on the go and have it automatically transcribed. Grab a photo of a poster, receipt or document and easily organize or find it later in search.
> 
> Capture what’s on your mind
> • Add notes, lists and photos to Google Keep. Pressed for time? Record a voice memo and Keep will transcribe it so you can find it later.
> 
> Share ideas with friends and family
> • Easily plan that surprise party by sharing your Keep notes with others and collaborating on them in real time.
> 
> Find what you need, fast
> • Color code and add labels to notes to quickly organize and get on with your life. If you need to find something you saved, a simple search will turn it up.
> 
> Always within reach
> • Keep works on your phone, tablet, computer and Android wearables. Everything you add syncs across all of your devices, so your thoughts are always with you.
> 
> The right note at the right time
> • Need to remember to pick up some groceries? Set a location-based reminder to pull up your grocery list right when you get to the store.
> 
> Available everywhere
> • Try Google Keep on the web at http://keep.google.com and on your Android phone by downloading the app at http://g.co/keep.
> 
> 
> What's new:
> Better organization
> • Organize your notes by adding labels to them. Labels are quickly accessible in the main menu.
> • Add recurring reminders to never miss regular to-dos.

Traceback (most recent call last):
  File "/Users/sqsgalaxys/Downloads/MeProjects/untitled1/pythonGetChromeWebstore.py", line 259, in <module>
### [Error 404 (Not Found)!!1](https://chrome.google.com/webstore/detail/hndaocghiemhpbpompakolklinipbifn '0.0')
    print("介绍: " + soup.find_all("pre", class_="C-b-p-j-Oa")[0].text)
IndexError: list index out of range

Process finished with exit code 1




/usr/local/bin/python3.6 /Users/sqsgalaxys/Downloads/MeProjects/untitled1/pythonGetChromeWebstore.py
### [Tunnello VPN - Unblock, Ultra-Fast & Secure! - Chrome Web Store](https://chrome.google.com/webstore/detail/hoapmlpnmpaehilehggglehfdlnoegck '0.0')
> 介绍: Up to 6 GB of free data per month (200 MB per day).
> Discover the Next Generation of VPN. Try Tunnello for free! When other VPN & Proxy are slow or unsecure, Tunnello is Ultra fast and perfectly secure. In two clicks, unblock any websites, app & secure your connection. Access anything blocked in your country, school or company.
> All your data pass through an encrypted tunnel over an RSA-4096 bits certificate for key exchange which makes your connection uncrackable! 
> Tunnello is simple, fast & secure.
> 
> Tunnello is the newest startup that will change the VPN industry. In only 4 months 100 000 users are using Tunnello VPN on their browser.
> Tunnello is 10x faster than a VPN and and still as secure. Tunnello for Chrome is an incredibly simple Google Chrome browser extension that can help you for:
> 
>   ● Unblock websites and apps
> Enjoy your favorite streaming entertainment, social networking and VoIP calling applications from anywhere in the world. Unlock Facebook, Twitter, YouTube, Spotify, Skype, Instagram, Snapchat and much more with a single click.
> 
>   ● Prevent piracy and spying:
> Hide your address IP and secure your connection by encrypting all your data. Nobody will have access to our information, especially when connected to a public Wi-Fi hotspot. Our VPN extension for Chrome is your personal protection for the access points.
> 
>   ● Surfing anonymously:
> Prevent government agencies, ISP (Internet Service Provider) and website owners to track your steps on the web. Hide your IP address and your digital identity to prevent the tracking and targeted advertising. Browse the internet privately and stay anonymous
> 
>   ● Change virtually your location
> You might want to change your internet location in order to access websites, apps or just change your IP address. Choose over 14 countries, change your location virtually and access any content worldwide.
> 
>   ● Bypass pricing discrimination on the Internet:
> Change your IP address for great savings on flights, car rentals, subscriptions, software and more
> 
> Browse in peace with Tunnello, follow these steps:
> - Install Tunnello
> - go on a blocked website
> - connect Tunnello and unblock-it!
> 
> 
> Try the new alternative to other VPN and Proxy:
> 
> Tunnello VPN is faster than any VPN or Proxy like Tunnelbear, Hotspot Shield, StrongVPN, Unblock Us, Zenmate, NordVPN, Le VPN …
> Tunnello give you Free data not like Hide My Ass, Vypr VPN, Gom VPN, Total VPN
> Tunnello is secure and do not use or resell your bandwidth like Hola does.
> Unlike Surfeasy, we offer unlimited bandwidth and do not distribute any advertising. 
> 
> Have you ever encountered issues watching a video on Youtube or a TV channel because of region restriction? Or simply having websites blocked because of internet censorship?
> Tunnello is here to help you!
> 
> Support
> Tunnello is simple and very stable, if you have any issue check out the faq: https://tunnello.com/faq/
> We also have a dedicated support Team that can help you 365 days / year.

### [Dyslexia - Chrome Web Store](https://chrome.google.com/webstore/detail/hocikkbhhnohmdfcoljccffnggiaaodl '0.0')
> 介绍: Help you to read fluently！
> This update simplifies the operation logic:
> 1. Enter read mode, you just need to remember double-click the article (can be set to double-click, three-click, four-click).
> 2. Delete click icon and right click operation.
> 3. Add a blacklist, the blacklist of sites will not load the extension.

### [SimilarWeb - Traffic Rank & Website Analysis - Chrome Web Store](https://chrome.google.com/webstore/detail/hoklmmgfnpapgjgcpechhaamimifchmp '0.0')
介绍: Use SimilarWeb’s browser add-on to get in-depth traffic and engagement statistics with a single click.
 
Find out how popular any website is and get instant knowledge and estimation on sources of traffic bringing users to the site. Check out SimilarWeb.com for much more in-depth analysis of websites and apps. 
When downloading our product you join SimilarWeb Panel and become part of our ambitious project of getting the insight and trends about the digital world this project is here to improve and expand the world’s knowledge about digital trends.
 
For the purpose of providing you with analytic data, ranks, popularity, similarity and website metrics, Usage of the extension requires granting it permission to capture anonymized click stream data. We will collect data regarding your browsing usage, specifically the domains you browse. For more information regarding our data collection, we urge you to review our privacy policy before you install our add-on, available here: https://www.similarsites.com/privacy-policy
### [一键发送到Kindle - Chrome Web Store](https://chrome.google.com/webstore/detail/hpphpohoimhpjigccjejlokfkdiaopof '0.0')
> 介绍: 通过该扩展，可以一键将选取的网页内容发送到您的 Kindle 设备，如果没有选取内容，则会由扩展自动选取全部正文。使用前请在扩展选项里输入您的亚马逊邮箱，并在亚马逊网站将 kindle@yiest.com 添加到 Kindle 推送的允许列表中。

### [JSON-handle - Chrome Web Store](https://chrome.google.com/webstore/detail/iahnhfdhidomcpggpaimmmahffihkfnj '0.0')
> 介绍: 对JSON格式的内容进行浏览和编辑，以树形图样式展现JSON文档，并可实时编辑。
> 
> Edit and browse JSON document in a node tree diagram.
> 
> After installed, open the URL will trigger JSON-handle:
> 安装后打开下面网址可以看到JSON-handle启动的效果：
> http://jsonhandle.sinaapp.com/demo.json
>  
> 

### [Cato - Chrome Web Store](https://chrome.google.com/webstore/detail/icphdcfpompgbdikholnedfeidemgobg '0.0')
> 介绍: Cato is command launcher for your web browser. Give Cato an action you'd normally do with your mouse or keyboard short and it will do it for you. The days of remembering keyboard shortcuts and excessive mouse use are over.
> 
> Feature List:
> - Bookmark and un-bookmark pages
> - Create new windows & tabs (including incognito)
> - Close tabs (single or multiple)
> - Copy the current URL
> - Calculate numbers with the built-in calculator
> - Change tabs
> - Detach tabs from their windows
> - Disable/Enable/Uninstall Extensions
> - Duplicate the current tab
> - Copy current URL
> - Detach tabs
> - Find bookmarks and open them
> - Play/Pause videos
> - Sort open tabs by URL
> - Merge all browser windows into one.
> - Open your Bookmarks, Downloads, History and Settings pages
> - Toggle Bookmark
> - Navigated your Pages & Tabs (Forward and back)
> - Mute tabs
> - Toggle Fullscreen mode
> - Reload tabs (single or multiple)
> - Search Google, Youtube and Gmail (more coming soon)
> 
> KEYBOARD SHORTCUT
> Activate the Extension by using [Command+J] on Mac & [Control+J] on Windows or Linux or assign your own custom command (https://goo.gl/Hv4YHc)

### [Learn2Code - Chrome Web Store](https://chrome.google.com/webstore/detail/idhfedcfngiegcjcplaognlconkojkom '0.0')
> 介绍: Learn2Code provides a way for users to compile and run their programs from within the browsers.
> 
> Features:
> * Compile and test your code from within the browser.
> * Support for 13 major programming languages(C/C++/Java/Python/C#/Perl/Ruby/Scala/Clojure/Haskell/Go/Erlang)
> * Syntax highlighting for all supported languages.
> 
> Upcoming features:
> * Save/Load the code from local file system.
> * Clean and intuitive UI design.
> 
> Source code:
> https://github.com/sridhar87/Learn2Code
> If you are a developer, feel free to contribute to this project, and give me a pull request, I will update the extension and will include your name in the list of contributors.
> 
> Credits:
> The online compiler is powered by hackerrank.com backend and the code editor is powered by ACE javascript editor.

### [Sound Pirate - Chrome Web Store](https://chrome.google.com/webstore/detail/idleenniidjlnmnjkjmmnocnkmjibadd '0.0')
> 介绍: Chrome extension to download online music. Supports bandcamp.com grooveshark.com, and many others. For Chinese users, it supports xiami.com, douban.fm, Jing.fm and most popular sites.
> 
> usage:
> 1. Update your chrome. Known supports 24+ version.
> 2. Install me.
> 3. Open online music and play music.
> 4. When music begins, download link will show on left/right corner. Click to download.
> 
> any suggestion/bug/discuss feel free to mail to lishi1608(at)gmail(dot)com

### [AutoPagerize - Chrome Web Store](https://chrome.google.com/webstore/detail/igiofjhpmpihnifddepnpngfjhkfenbp '0.0')
> 介绍: 

### [Reader View - Chrome Web Store](https://chrome.google.com/webstore/detail/iibolhpkjjmoepndefdmdlmbpfhlgjpl '0.0')
介绍: Updates:
v0.1.2：
fix bug for Chrome 50.


Make web articles in a comfortable reading view like the Safari's Reader View style. The extension icon will display in the address bar when you visiting a article page, click it to enjoy reading.

For keyboard shortcuts setting, go to extensions manage page, click the link at the bottom right of the page to open. (or just visit chrome://extensions/configureCommands).

Enjoy~
### [SimpRead - Reader View - Chrome Web Store](https://chrome.google.com/webstore/detail/ijllcpnolfcooahcekpamkbidhejabll '0.0')
> 介绍: 让你瞬间进入沉浸式阅读的 Chrome 扩展，类似 Safari 的阅读模式。
> 
> 简悦取自 - 【简】单阅读，愉【悦】心情 之意。
> 
> *** 简悦的宗旨 ***
> 
> 还原阅读本质，提升阅读体验。
> 
> 在【知识爆炸 / 信息过载】的当下，如果你有与我一样的【阅读障碍】，相信 【简悦】会对你所有帮助。
> 
> *** 主要功能一览 ***
> 
> - 阅读模式；
> - 聚焦模式；
> - 支持任意页面的临时阅读模式；
> - 支持【论坛类页面】与【分页功能】如：知乎 · 百度贴吧等；
> - 支持【自动生成目录】与 【TXT 阅读器】；
> - 可导入多个适配源的适配源管理器，可编程的站点编辑器，站点管理器；
> - 多种主题；
> - 更符合【中文阅读习惯的设置】，包括：【字间距、行间距】等以及【自定义 CSS】
> - 丰富的导出功能，包括： Markdown · PNG · PDF · Epub · Send to Kindle · Pocket · Instapaper · Linnk · Dropbox · Onenote · Google Drive · 印象笔记 / Evernote
> - 同步、上传/下载 配置、同步适配列表、快捷键等；
> - 高级定制，包括：右键菜单、控制栏可隐藏、阅读进度可隐藏、自动进入阅读模式、白名单以及 排除列表（黑名单）；
> - 稍后读；
> 
> *** 详细功能 ***
> 
> http://ojec5ddd5.bkt.clouddn.com/feature%201.1.0.png
> 
> *** 照片集 ***
> 
> http://ksria.com/simpread/gallery/
> 
> *** 关于安全性  ***
> 
> 代码已公开 https://github.com/kenshin/simpread
> 
> *** Telegram 群  ***
> 
> https://t.me/simpread
> 
> *** 问题反馈  ***
> 
> https://github.com/kenshin/simpread/issues
> 
> *** 联络方式  ***
> 
> http://kenshin.wang | kenshin@ksria.com
> 
> *** 更新日志 ***
> 
> http://ksria.com/simpread/changelog.html

### [划词翻译 - Chrome Web Store](https://chrome.google.com/webstore/detail/ikhdkkncnoglghljlkmcimlnlhkeamad '0.0')
> 介绍: 一个简便但强大的翻译扩展。
> 
> 注意:扩展对Chrome商店无效是因为Chrome自身的安全限制，请在别的网站测试！测试之前请先刷新网页！
> 
> 为什么选择划词翻译？
> 
>   - 支持几乎所有语言的翻译与阅读，并且同时支持国内与国外的谷歌翻译；
>   - 划词即显示翻译结果，简单方便。可以指定目标语言，例如从中文翻译到法语；
>   - 支持在 PDF 文档里使用
>   - 单词释义既详细又精准；
>   - 自带多种网页翻译，弥补国内Chrome网页翻译总是出错的不足；
>   - 完全免费；
>   - 无需安装任何第三方软件，麻雀虽小，五脏俱全。
> 
> 为了保证扩展的质量，我挤出了不多的空闲时间，如果你觉得这个扩展很好用，请给五颗星~
> 
> 详细说明请查看：http://t.cn/RqpoGU4

### [Darkness - Beautiful Dark Themes - Chrome Web Store](https://chrome.google.com/webstore/detail/imilbobhamcfahccagbncamhpnbkaenm '0.0')
> 介绍: Darkness provides beautiful dark themes for popular websites, significantly reducing eye strain and fatigue caused by a bright screen.
> 
> It comes with dark themes for Google and Facebook. Pro upgrade ($5) adds support for YouTube, Gmail, Google Docs, Reddit, Twitter, Messenger, Inbox, Dropbox, GitHub, Trello, StackOverflow and more.
> 
> ✔ Great looking themes (not inverted colors)
> ✔ Handcrafted by designers
> ✔ Reduces eye strain, fatigue & headaches
> ✔ Eliminates annoying glare
> ✔ Helps you sleep faster and better
> 
> Darkness features 5 designer-made themes:
> ► Iceberg
> ► Tomorrow (Pro only)
> ► Material Design (Pro only)
> ► Dusk (Pro only)
> ► Red Alert (Pro only)
> 
> How to configure Darkness?
> 1. Visit a supported website like Facebook or Google.
> 2. Click the moon icon in the top-right corner of the website.
> 
> We care about our users - Darkness is 100% clean, adware and spyware free.
> 
> Darkness is an open source project, available on GitHub: https://github.com/liorgrossman/darkness

### [Minimal New Tab Clock - Chrome Web Store](https://chrome.google.com/webstore/detail/impmanfocmgfodfbnhbmkkonnpcogfak '0.0')
> 介绍: Minimal clock, minimal settings, minimal fuss.
> 
> V1.4.1
> 
> - Show correct version number
> 
> 
> V1.4
> 
> - Added a theme picker
> - Custom colour can be picked from the theme picker
> - Current day now updates when your system clock changes to the next day
> - Minor performance improvements
> 
> 
> V1.3.2:
> 
> - Fixed 12AM showing as PM
> 
> 
> V1.3.1:
> 
> - Fixed an issue with 12hr format clock and AM/PM display
> - Performance improvements
> - Fixed keyboard interaction issues
> - Added a link to colour change functionality questionnaire
> 
> 
> V1.3:
> 
> - Removed leading zero on 12hr format
> - Moved second hand to the top of the stack
> 
> 
> V1.2:
> 
> - Dark theme (click the lightbulb to use)
> - Analogue clock
> - 12 hour digital clock

### [Send to Kindle (by Klip.me) - Chrome Web Store](https://chrome.google.com/webstore/detail/ipkfnchcgalnafehpglfbommidgmalan '0.0')
> 介绍: Send to Kindle is a Browser extension for Kindle owners who prefer reading web content on their devices. It’s designed to offer a quick way for pushing web content to Kindle, so you can read articles or news later on your device.
> 
> Our new App - Ziin ( http://www.ziin.me/ ), a Google Reader Client on iPad, specially optimized for reading. It also can send articles to your Kindle.
> 
> *NEW* Available for Safari, Firefox, Opera, IE9: http://www.klip.me/
> 
> *NEW* Google Reader to Kindle (http://www.klip.me/googlereader/)
> 
> *IMPORTANT* Once the extension is installed, it will only work on newly opened pages (or you can refresh the page)
> 
> 
> Changelog
> 2.6.x Optimized for Metafilter (Thanks Luke)
> 2.4.x Read your favorite articles on Android (http://www.klip.me/readit/android/)
> 
> Features
> * Push web articles to your Kindle instantly
> 
> * Automatically detect the main content and send to Kindle, just 1-click
> 
> * It's fast and easy to delete ads, blank and other junk you don't want.
> 
> * Optimized for Google Reader, Wikipedia, Quora, Hacker News, and Stack Exchange network of Q&A websites, Metafilter
> 
> * It's Free!
> 
> 
> Usage
> Automatic: Directly click the "Send to Kindle" button, auto grab the main content and send it to Kindle
> 
> Manual: Manually select the page content first, click the "Send to Kindle" button, and send the current selection to Kindle
> 
> Generally about 1-5 minutes you can receive article in Kindle
> 
> Keyboard shortcuts
> Preview: Ctrl-F12
> Send: Alt-Ctrl-K
> Send Later: Alt-Ctrl-S
> 
> Setup
> Open "Options" Page, setup your Kindle's email address
> 
> Known issues:
>   - Doesn't work on Google Chrome extension gallery pages (including this page).
> 
> * Send to Kindle DOESN'T ACCESS TO ANY COOKIE OF THE USERS.
> 
> * This extension is under continuous development. Any feedback is highly welcome and will help us in adding new features.
> 
> * I'd appreciate if you rate it, tell your friends, write/blog/tweet about it!
> 
> Email: support@klip.me

### [Hacker News Stack - Chrome Web Store](https://chrome.google.com/webstore/detail/jcdfcpjmfpbnimkdackbcmdgdpoeklio '0.0')
> 介绍: This extension will take the news items you have clicked on to the bottom of the hacker news website, making you focus on the unread items. This works only in the hacker news website, and is it acts on the current batch of items being displayed.
> 
> The ycombinator's hacker news website is a mess in terms of semantic html, so please feel free to report any bugs to help me improve this extension.
> 
> PS. If you have other Hacker News extensions installed that change in anyway the html of the page, this extension won't work!
> 
> Known issues:
> 
> - If you open a link with right-click -> "open link in new tab" the item doesn't get marked as read. Use middle click instead (Cmd+click on mac) - Currently working on this.

### [Browser Alfred - a command launcher - Chrome Web Store](https://chrome.google.com/webstore/detail/jglmompgeddkbcdamdknmebaimldkkbl '0.0')
> 介绍: Full version: Steward
> 
> Document: http://oksteward.com/steward-document-en/
> 
> update:
> v3.2.7 -- see update tab
> 
> feature:
> workflow: custom your combination of commands
> help show help
> on enable an extension
> off disable an extension
> set open extension's option page
> del delete an extension
> run launch an app
> tab find a tab and goto
> his find in history and goto
> bm find in bookmark and goto
> dl find in downloads and open folder
> yd youdao translator
> po search your pocket article
> todo todolist
> bk block an url
> 

### [Voblet - Chrome Web Store](https://chrome.google.com/webstore/detail/jgnennkfpahpjpbmbbodaipgoilccmco '0.0')
> 介绍: ** New feature : Bookmarking for Github **
> Latest voblet update enables bookmarking feature for github. Bookmark your favorite repositories and organize them with custom tags.
> 
> 
> Features :
> 
> - Save webpages to view later
> - Send links between your devices
> - Access saved links on your phone
> - Bookmarking for Github
> 
> Save webpages to view later:
>     Save your favorite articles, videos etc to view them later. Bookmark the links and organize with custom tags.
> 
> Send links between your devices:
>     Voblet connects your devices. Send links from browser to your phone with just a click. You can push links from your phone to browser with just a tap. No more emails to send links :)
> 
> Access saved links through your phone: 
>    The links you saved from the browser are accessible from your phone.
> 
> Bookmarking for Github :
>     Bookmark your favorite repositories with a click and organize them with custom tags.
> 
> Have any suggestions ? drop a mail to feedback@voblet.com
> 
> 
> For updates
> follow us on twitter - https://twitter.com/vobletapp
> like us on facebook - https://www.facebook.com/voblet

### [Chrome extension source viewer - Chrome Web Store](https://chrome.google.com/webstore/detail/jifpbeccnghkjeaalbbjmodiffmgedin '0.0')
> 介绍: View the source code of any Chrome extension in the Chrome Web store without installing it.
> 
> Features:
> - Button at the Chrome Web store
>   - Download extension as zip file
>   - View source
>   - Configurable via context menu on button: Set one-click action via "primary action on click".
> - View source:
>   - File name/type filter
>   - Search in the file content (literal or regexp)
>   - Automatic beautification (formatting) of code
>   - Syntax highlighting
>   - Show hashes (md5, sha1, sha256, sha384, sha512) of individual files
>   - Image preview
>   - View embedded zip files
>   - View any zip file by URL or file chooser
>   - View source of platform-specific extensions (such as Chrome OS-only extensions, or NaCl for a different architecture).
> - Full support for incognito mode.
> - Outputs public key and extension ID to the console.
> 
> Optional features (see options page):
> - View source of Opera 15+ extensions or Firefox addons.
> - "View extension source" contextmenu item on links to Chrome extensions
> - View source of Chrome extensions outside the webstore. The View source button becomes visible when you select a CRX file for download.
> 
> Source code: https://github.com/Rob--W/crxviewer
> Online demo: https://robwu.nl/crxviewer/
> Contact: rob@robwu.nl
> 
> Change log:
> - 1.2.3:
>  Add "downloads" permission to make sure that the "Download" button always works as intended.
> - 1.2.4:
>  Add extra parameters to the CRX URL to make sure that CRX files of extensions uploaded to the Chrome Web Store after July 2014 are correctly read.
> - 1.2.6: Sync options, use optionsV2, show numeric progress instead of dots, updated JSBeautifier, restore font size.
> - 1.2.7: Bugfixes (viewer height, checkbox filter).
> - 1.3:
>  Support Firefox addons (also available as a Firefox addon!)
>  Search within files
>  Customize webstore download parameters
>  View embedded zip files and any zip file
> - 1.3.1: Use correct URL for loading extension files.
> - 1.3.2: Bugfix to allow unusual extension URLs to be opened again.
> - 1.4: New syntax highlighter, improved search controls, improved word wrap.
> - 1.5: Calculate hashes, add link to Github project page, bugfix for case-sensitive search.
> - 1.6: Improved search highlighting & also search in beautified content.
> - 1.6.2: Configurable "primary action on click", open new tab next to current tab.

### [Flappy Octocat - Chrome Web Store](https://chrome.google.com/webstore/detail/jjjhhlomhbdmnfgaccmddhmjfeekjlbl '0.0')
介绍: a chrome extension to play a flappy bird like game on github contributions board
### [You are Awesome - Chrome Web Store](https://chrome.google.com/webstore/detail/jkhopfdenimipdamjmfpijifmmpnakpc '0.0')
介绍: Even if the world lets you down, Smiley face believes in you! Therefore, you are AWESOME!
### [Todoist: To-Do list and Task Manager - Chrome Web Store](https://chrome.google.com/webstore/detail/jldhpllghnbhlbpcmnajkpdmadaolakh '0.0')
介绍: Join the 10million+ people around the world who are accomplishing amazing things with Todoist – the simple, yet powerful task manager built for the pace of modern life. Whether you need to collaborate with your team, keep track of your most important projects, or just remember to pay the rent, Todoist is there to help give you peace of mind.

Praised as a life-changing app by The Guardian, USA Today, the New York Times, The Wall Street Journal, Forbes, Lifehacker and more, Todoist works seamlessly across 10+ different platforms in 20 languages so you can stay motivated and productive no matter where you are.

“If you're looking for a to-do app that works on all your devices, has great features for monitoring your productivity, and lets you geek out with how you organize your tasks, Todoist is the app for you.”  - PC Mag

MANAGE ALL YOUR TASKS RIGHT FROM YOUR BROWSER
Download our Chrome extension to keep your to-do lists just a click away. View, add, organize, complete, and delegate tasks right from your browser.

SAVE WEBSITES AS TASKS
▸ Save websites as tasks with a single click. Your task will link back to the original web page so you can quickly access it when you need to. 
▸ Save articles to read for later
▸ Save Amazon pages for gift ideas
▸ Save IMDB pages to a Movies list 
▸ Save Google Docs for future reference

With Todoist on all your devices you can…

MANAGE YOUR TASKS FROM ANYWHERE - EVEN OFFLINE
Add, complete, and re-schedule tasks from your phone, tablet, desktop, browser, email, and more - even offline! With an automatic, 24/7 sync across all your devices, you’ll never lose track of your to-do list. 

PLAN AHEAD AND NEVER MISS ANOTHER DEADLINE
Keep track of your important deadlines with due dates and recurring dates. Quickly view and prioritize your tasks for the day or week ahead with visual, drag-and-drop scheduling. 

ORGANIZE AND PRIORITIZE YOUR WORK
Take your to-do list organization to the next level with sub-tasks, task priorities, sub-projects, and color-coded projects. Whether you practice the GTD® productivity method or just want to keep a simple list of errands,Todoist is flexible enough to handle any workflow. 

COLLABORATE SEAMLESSLY
Whether you’re coordinating a big project or sharing a grocery list, Todoist makes communication easy. Share projects, assign tasks, and add comments all within the app. Instant notifications will keep you up-to-date whenever changes are made. 

STAY MOTIVATED AND PRODUCTIVE 
Track, measure, and “gamify” your productivity with Todoist Karma. Accumulate points by setting and meeting weekly/monthly goals. Visualize your progress with beautiful graphs color-coded by project.

BOOST YOUR PRODUCTIVITY WITH PREMIUM
▸ Set up and receive push notifications, email or SMS reminders based on your physical location or the date and time.
▸ Get even more organized using task notes, enhanced labels, and powerful filters.
▸ Upload files, sound recordings and photos to your tasks from your computer, Dropbox, or Google Drive. 
▸ Add tasks by email and access your to-do list on your iCalendar.
▸ Track and improve your productivity with extended Todoist Karma features.
▸ And much, much more!

Sign up, log in and let go of stress. For more information visit www.todoist.com. 
### [crxMouse Chrome™ Gestures - Chrome Web Store](https://chrome.google.com/webstore/detail/jlgkpaicikihijadgifklkbpdajbkhjo '0.0')
介绍: Boost browsing productivity with mouse gesture navigation shortcuts - simple Mouse Gestures, Super Drag, Wheel Gestures, Rocker Gestures.

crxMouse Chrome™ Gestures enables mouse navigation with amazing features:

★ Simple Mouse Gestures, Super Drag, Wheel Gestures, Rocker Gestures

★ Fully customizable mouse gestures, keystrokes, actions and mouse movements

★ Windows, Linux and Mac support

★ Import and Export Configuration 

Make it happen with a mouse gesture! crxMouse Chrome™ Gestures extension brings the power of the Chrome browser to your fingertips, boosting your productivity by unlocking fully customizable mouse gestures, keystrokes, and mouse shortcuts. 

The power of this mouse gestures extension makes navigation simple!
 
**crxMouse Chrome™ Gestures is forever free. No paid edition or account, no advertisements. 
Please note: Mouse gesture navigation doesn't work on Chrome's built-in pages because of Google's security restrictions.

Mouse Gestures, Built-in Actions:
Press + Hold Right Button (anywhere on the screen) and Drag to perform the following gestures with your mouse: 
↓→ : close current tab
↓→↑ : open a new window
← : back
←↑ : reopen closed tabs
→ : forward
→↓ : scroll to bottom
→↑ : scroll to top
↑ : scroll up one page
↑↓ : refresh
↑↓↑ : force a refresh
↑← : move to the left tab
↑→ : move to the right tab
↓→↓ : close current window

Super Drag Built-in Actions:
Press + Hold Left Button and drag links to perform the following actions:
→ : open link in a new tab
← : open link in a new tab (background)
←↓→ : copy text
→↓← : copy URL
Press + Hold Left Button and drag text to perform the following actions:
← : search in new tab (background)
→ : search in a new tab

Wheel Gestures Built-in Actions:
Press + Hold Right Button and scroll to perform the following actions:
↑: scroll to top
Press + Hold Left Button and Scroll to perform the following actions:
↓: scroll to bottom
 

Important note
Our users help CrxMouse Chrome™ Gestures provide the best and most popular mouse gestures for any given site. In order to identify the best gestures from the CrxMouse database, we collect anonymized browsing data. We care greatly about your privacy. For more information, please read our privacy policy at: https://crxmouse.com/privacy/


Version History:
3.0.0 - Added ability to see top used gestures.
2.9.2 - Minor bug fixes
2.9 - Major bug fixes
2.7.8 - Bug Fixes
2.7.6 - Bug Fixes
2.7.5 - Added French translation and minor bug fixes
2.7.3 - Bug Fixes and new video!
2.7.2 - Bug Fixes
2.7.1 - Bug Fixes and improved UI, and again thanks to your feedbacks
2.6 - Bug Fixes, we really appreciate your help and feedback!
2.5 - Bug Fixes, thanks for all the feedbacks
2.4 - New Name: CrxMouse!
2.1 - Bug Fixes, thanks for all the feedbacks
2.0 - Complete rewrite of the code to achieve maximum productivity and stability

### [取字-快速识别,一秒取字 - Chrome Web Store](https://chrome.google.com/webstore/detail/jmonhcfndjifnfldnaknlpgpfjlgpiig '0.0')
> 介绍: 您可以利用这款插件在线把图片或者视频中的文字进行截取并自动识别，数秒之内即转换为可编辑操作的文本，提高工作效率，目前这款插件支持识别中文和英文两种语言，并可兼容所有版本的Chrome浏览器。

### [LiveReload - Chrome Web Store](https://chrome.google.com/webstore/detail/jnihajbhpnppcggbcgedagnkighmdlei '0.0')
> 介绍: Provides Chrome browser integration for the official LiveReload apps (Mac & Windows) and third-parties like guard-livereload and yeoman.
> 
> See livereload.com for details; visit feedback.livereload.com to get help and vote for new features.

### [Quick Tabs - Chrome Web Store](https://chrome.google.com/webstore/detail/jnjfeinjfmenlddahdjdmgpbokiacbbb '0.0')
> 介绍: # INTRODUCTION
> 
> Quick Tabs is a tab management browser extension for the Google Chrome web browser based on the "Recent Files" quick selector built into the excellent IntelliJ IDEA by Jetbrains.
> 
> Quick Tabs allows you to move quickly between recently used tabs without requiring the use of your mouse, locate and switch to tabs as you need them with minimal keystrokes even when you have large numbers of open tabs.
> 
> Visit the [Quick Tabs](https://chrome.google.com/extensions/detail/jnjfeinjfmenlddahdjdmgpbokiacbbb) google extensions page to install this and try it out ...
> 
> 
>  FEATURES
> 
> * Lists all the open tabs in Chrome across all of your open windows
> * Tabs are listed in most recently used (MRU) order and excludes the current tab (since you're switching tabs)
> * Fuzzy search your bookmarks:
>   * Bookmarks are automatically searched when only a few tabs match your search string
>   * Add a space at the start or end of your search string to search bookmarks along with tabs
>   * Add two spaces at the start or end of your search string to search only bookmarks
> * Fuzzy search your browser history:
>   * Add three spaces at the start or end of your search string to search browser history
> * Find noisy tabs by searching for '<))' (then close them all with shift+ctrl+d ;-))
> * Chrome keyboard shortcuts (configured using the keyboard shortcuts dialog at the bottom of the Chrome Extensions page):
>   * Shortcut key to launch popup window from most tabs (default ctrl+e, cmd+e on Mac, ctrl+q on Linux).
>   * Select previous tab without loading the popup window (unmapped by default)
>   * Select next tab without loading the popup window (unmapped by default)
>   * IMPORTANT the 'next tab' shortcut is only available for a second or so (while the badge text is orange) before the current tab is moved to the top of the MRU list.
> * Tab list popup shortcut keys:
>   * Select previous tab (same as Chrome keyboard shortcut or up arrow)
>   * Select next tab (same as Chrome keyboard shortcut or down arrow)
>   * Switch to selected Item (enter)
>   * To close selected tab (default ctrl+d, see extension options)
>   * To close ALL displayed tabs in the tab list, honors search filtering (default shift+ctrl+d, see extension options)
> * Displays the number of tabs you currently have open in all your Chrome windows
> * Quickly search and select tabs by typing letters in the page title or url
> * Track recently closed tabs and allow them to be searched and restored
> * Popup customization using css
> 
> 
>  PERMISSIONS
> 
> Quick Tabs requires the following:
> 
> * **Read and change your browsing history**: _read only_ access is required to record your open tabs and search browser history.
> * **Read and change your bookmarks**: _read only_ access is required to search and display your bookmarks.
> 
> 
>  SCREENSHOTS
> 
>  Quick Tabs ready for action.
> 
> ![Popup Screenshot](screenshots/in_action.png?raw=true)
> 
>  Tab and bookmark search.
> 
> ![Search Screenshot](screenshots/searching_tabs.png?raw=true)
> 
>  History search.
> 
> ![Search History](screenshots/searching_history.png?raw=true)
> 
> Search your browser history by adding 3 spaces to the start or end of your search query.
> 
>  Decide what to show.
> 
> ![Search History](screenshots/go_minimal.png?raw=true)
> 
>  Custom CSS styling.
> 
> ![Search Screenshot](screenshots/custom_css.png?raw=true)
> 
> In this case https://userstyles.org/styles/99938/better-styling-for-chrome-extension-quick-tabs by @Bunnyslippers
> 
> 
>  SOURCE
> 
> The source code for this extension is available on [github](http://github.com/babyman/quick-tabs-chrome-extension), please feel free to inspect it before you install this extension, especially as I am asking permission to interact with your computer and its private data.
> 
> You can also install it manually if you want to be certain that the source code on github is directly what you install. Note, this will NOT automatically update the extension when bugs are fixed and features are added.
> 
> In your terminal, `cd` to the folder you want to clone it to, and run `git clone https://github.com/babyman/quick-tabs-chrome-extension`. Then in Google Chrome, click `Window - Extensions`, click the checkbox called "Developer Mode", and click the "Load unpacked extension" button. Navigate to the cloned project, and select the "quick-tabs" folder. You now have the plugin loaded as a developer. Again, this will NOT automatically update the extension when bugs are fixed and features are added.
> 
> 
>  FEEDBACK AND BUGS
> 
> Please report all your valuable feedback, feature requests and bug reports on the github [issues page](http://github.com/babyman/quick-tabs-chrome-extension/issues) for this extension.
> 
> 
>  RELEASE NOTES
> 
> 2017.10.8 - fixed scrolling issue (fixes #195)
> 0.9.6 - reduced popup size when few tabs are open
> 0.9.5 - fixed missing scrollbars on Linux
> 
>  ACKNOWLEDGEMENTS
> 
> Inspired by
> http://www.jetbrains.com/idea/
> 
> Icon image based on photo by Ged Carroll found at
> http://www.flickr.com/photos/renaissancechambara/3380657988/
> 
> Blank Icon by Deleket (Jo)
> http://deleket.deviantart.com/
> 
> 
>  LICENSE
> 
> Copyright (c) 2009 - 2017, Evan Jehu
> All rights reserved.
> 
> Redistribution and use in source and binary forms, with or without modification, are permitted provided that the following conditions are met:
> 
> * Redistributions of source code must retain the above copyright notice, this list of conditions and the following disclaimer.
> * Redistributions in binary form must reproduce the above copyright notice, this list of conditions and the following disclaimer in the documentation and/or other materials provided with the distribution.
> * Neither the name of the author nor the names of its contributors may be used to endorse or promote products derived from this software without specific prior written permission.
> 
> THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL EVAN JEHU BE LIABLE FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
> 

### [GHDB - Chrome Web Store](https://chrome.google.com/webstore/detail/jopoimgcafajndmonondpmlknbahbgdb '0.0')
> 介绍: Google Hack Data Base - application to work with GHDB. Choose a category and click on the necessary query.  To find description vulnerability, click "Search on www.exploit-db.com". Application provides possibility to search vulnerabilities on the specified site. Just click on the search button and enter the site name. This application allows a better understanding of the basis web security.

### [Mail Checker - Chrome Web Store](https://chrome.google.com/webstore/detail/kaklalnjjcbnacalpghdfokeohelpbnf '0.0')
> 介绍:  * 2014-12-19 v2.4:
>    * fix netease entry
> 
>  * 2014-12-03 v2.3:
>    * fix yeah js6 support
> 
>  * 2014-12-02 v2.2:
>    * fix netease js6 support
> 
>  * 2013-06-30 v2.1:
>    * fix qq mail
>    * upgrade manifest version 2
> 
>  * 2013-01-27 v2.0:
>    * fix netease js5 support
>    * only display inbox
> 
> 
> =supported mail list=
>  - mail.163.com
>  - www.126.com
>  - mail.qq.com
>  - www.yeah.net
> 
> =TODO=
>  - support multi-emails
> 
> 主要使用163邮箱，其他邮箱使用不多，如有问题：
>  - http://code.google.com/p/mail-checker/issues/list反馈

### [SimpTab - New Tab - Chrome Web Store](https://chrome.google.com/webstore/detail/kbgmbmkhepchmmcnbdbclpkpegbgikjc '0.0')
> 介绍: SimpTab - Minimalist Chrome new tab extension, hope to have good mood every time you open it. Removed redundant function, focused tab rendering.
> 
> Feature:
> https://github.com/Kenshin/simptab/blob/master/README.en.md
> - Automatic recognition languages. (Simplified, Traditional, English.)  
> - Daily / random to replace the background. (Note: The daily changing background only from Bing.com.)  
> - Multi background sources, including: bing.com, wallhaven.cc, unsplash.com, flickr.com, googleartproject.com, 500px.com, desktoppr.co, visualhunt.com, nasa apod, simptab images.  
> - Twenty-four solar terms.
> - Background loading progress. ( Lower left corner, only at load time. )
> - Support `shortcuts` / `omnibox` operation.
> - Notification. ( include: upload, favorite. )
> - Top sites. ( include: simptab, senior, hidden mode. )
> - Upload.
> - Favorite.
> - Pin.
> - Dislike.
> 
> Security:
> - Open source https://github.com/kenshin/simptab
> 
> Feedback:
> https://github.com/kenshin/simptab/issues
> 
> Contact:
> http://kenshin.wang | kenshin@ksria.com
> 
> CHANGELOG:
> https://github.com/kenshin/simptab/blob/master/CHANGELOG.md

### [Open Frame - Chrome Web Store](https://chrome.google.com/webstore/detail/kdhjgkkaacdhdioocfbpmhjidbinfajj '0.0')
> 介绍: Chrome recently removed the "Open frame in new tab", and related context menu items. This extension adds them back. It allows you to open a frame or iframe from any webpage in a new tab, new window, or new incognito window. Or you can copy the URL to the clipboard for later use.
> 
> Version 7 removes the need to have access to the URLs you visit, since the tabs extension API has been updated such that it is no longer required. Yay. It also fixes the bug where "open in this tab" did not work.

### [ES6 Tips - Chrome Web Store](https://chrome.google.com/webstore/detail/keaijnbjoibighkpmcgjdmpegbhfohjl '0.0')
> 介绍: 

### [Inoreader Companion - Chrome Web Store](https://chrome.google.com/webstore/detail/kfimphpokifbjgmjflanmfeppcjimgah '0.0')
> 介绍: This is the official browser extension for Inoreader - the content reader for power users who want to save time. 
> 
> Inoreader helps you keep track of your top information sources, monitor keywords or social feeds, save pages for viewing later and access all your articles anytime with powerful free search and full subscription archive.
> 
> With Inoreader Companion you can harness the full power of your reader while browsing any site on the web:
> 
>  ★ Keep an eye on the number of unread articles with the counter
>  ★ See a pop-up with your updated subscriptions and search within your content
>  ★ Subscribe to sites or save web pages for viewing later without interrupting your browsing experience
>  ★ Use Inoreader Companion to boost your productivity and save time!

### [Chromium Wheel Smooth Scroller - Chrome Web Store](https://chrome.google.com/webstore/detail/khpcanbeojalbkpgpmjpdkjnkfcgfkhb '0.0')
> 介绍: This extension changes scrolling on pages loaded by http and ftp very comfortable smooth one. You can design animation curve of scroll as you prefer by previewing plotted curve in the options page. It has bouncy edge feature also.
> 
> This is a port of a Firefox add-on that has same features: Yet Another Smooth Scrolling. If you like this extension, you should use YASS when you are on Firefox. 
> 
> 

### [Githunt - Chrome Web Store](https://chrome.google.com/webstore/detail/khpcnaokfebphakjgdgpinmglconplhp '0.0')
> 介绍: Githunt is an extension that replaces the new tab of your browser with the trending github repositories. 
> 
> You can look through the repositories for any technology of your liking and for any period of time. By default it shows the trending repositories (most starred repositories created in the given period of time) for the last week and as you keep scrolling, you will be presented with the popular repositories of the consecutive past weeks.
> 
> All you have to do is select how you would like to see the repositories (monthly, weekly or yearly) and the language, it will remember your choice and will show you the trending repositories in that category whenever you will open the new tab.

### [Play With Docker - Chrome Web Store](https://chrome.google.com/webstore/detail/kibbhpioncdhmamhflnnmfonadknnoan '0.0')
> 介绍: This chrome extension adds a "Try in PWD" button on any Docker Hub image page. By clicking this button the user is presented with defined stack files for the image. Then it is possible to just try any of the stacks with a single click on Play With Docker.

### [MBL百度网盘离线脚本 - Chrome Web Store](https://chrome.google.com/webstore/detail/kidicenkmkhnjipapnkomalnjobgefoi '0.0')
> 介绍: 此插件为了方便将百度公开的资源推送aria2（MBL）,此插件只是个外壳，作者是Mormts，我只是搬运工【感谢作者Mormts】，当然，其他路由或者NAS也可以用（只要装的是aria2当下载工具）, 欢迎入Q群讨论MBL:155847389，论坛：www.nasyun.com。

### [Tab Organizer - Chrome Web Store](https://chrome.google.com/webstore/detail/kkcbifggchajpkagcpagenpfghbplghc '0.0')
> 介绍: *** FEATURED ON PRODUCT HUNT AND LIFEHACKER ***
> 
> Organizes the unpinned tabs in the current window by grouping them by URL. Tabs from the same base URL (the same website) will be grouped together, and groups will be made in the order that the first tab from that group appears in the original order.
> 
> Use the extension by clicking its button, and it will rearrange the tabs in the current window, ignoring any pinned tabs.
> 
> * * * NEW IN VERSION 1.0: * * *
> * Options page to manage settings
> * Automatically sort tabs every 5, 30, or 60 minutes.
> * Keyboard shortcut "Ctrl + Shift + A" to sort on command.
> 

### [XSS Rays - Chrome Web Store](https://chrome.google.com/webstore/detail/kkopfbcgaebdaklghbnfmjeeonmabidj '0.0')
> 介绍: XSS Rays is a security tool to help pen test large web sites. It's core features include a XSS scanner, XSS Reverser and object inspection. Need to know how a certain page filters output? Don't have the source? No problem. XSS Rays will blackbox reverse a XSS filter without needing the source code.
> 
> You can also extract/view and edit forms non-destructively that normally can't be edited. For example if you want to modify the value of a checkbox without changing it's type XSS Rays can link to the object and allow you to change the value without altering the original object.
> 
> Using the object inspector you can browse through the window object and edit the contents of the functions in real time allowing you to dissect a web page and understand more how it works. This also works with globally defined functions, you can see which functions the developer has decided to place within the window object.
> 
> If you have ever wanted to search all files for a particular string, you can use the search feature to use regular expressions on all scripts and event handlers, highlighting the required keywords.

### [Raindrop.io New Tab / Speed Dial - Chrome Web Store](https://chrome.google.com/webstore/detail/knifgjkgmgdinjeecneiphoniamhgbof '0.0')
> 介绍: Features:
> - Feature-rich, attractive, easy-to-use bookmarks
> - Perfect for articles, gallery, sites
> - Share & collaborate
> - Web Clipper for fast save any pages
> 
> Our goals:
> - Speed (faster than default new tab page)
> - Material Design
> - Sync

### [Error 404 (Not Found)!!1](https://chrome.google.com/webstore/detail/kpamljbkjaaljbcgobdealnpalcgicna '0.0')
Traceback (most recent call last):
  File "/Users/sqsgalaxys/Downloads/MeProjects/untitled1/pythonGetChromeWebstore.py", line 259, in <module>
    print("介绍: " + soup.find_all("pre", class_="C-b-p-j-Oa")[0].text)
IndexError: list index out of range

Process finished with exit code 1




/usr/local/bin/python3.6 /Users/sqsgalaxys/Downloads/MeProjects/untitled1/pythonGetChromeWebstore.py
### [New Tab? Flag! - Chrome Web Store](https://chrome.google.com/webstore/detail/lagcgenebmlhjhclaoakigmljeipmamg '0.0')
> 介绍: Love flags? Me too! This is a Chrome extension that replaces Chrome's new tab page with a random country's flag and name. Featuring over 250 individual flags, you'll learn all of the flags of the world without even trying!
> 
> All flags are rendered in beautiful SVG, meaning HD presentation on any screen size.
> 
> If you enjoy the app please remember to rate and review!
> 
> NEW FEATURES!!!
> 1.0: Includes all flags of US states and Canadian provinces. These can be turned on and off in the settings.
> 1.1 Clicking on a country's label now brings you to its Wikipedia page
> 1.4 Additional flag packs: Australian states, supranational unions, and Soviet republics
> 
> Most graphics are from Wikimedia and are in the public domain. For full credits, see the repository:
> https://github.com/alecashford/vexilology_chrome_extension

### [Zoom for Google Chrome - Chrome Web Store](https://chrome.google.com/webstore/detail/lajondecmobodlejlcjllhojikagldgd '0.0')
> 介绍: It helps you to zoom easy in and out a web page. Thanks to the slider and the zoom buttons. It's the number one and best magnifying browser extension to customize the zoom value of that web page.
> 
> Zoom is a lightweight and useful add-in designed to get a perfect zoom experience. It works for all known sites such as YouTube, Vimeo, Yahoo, Amazon, Wikipedia, Facebook, Twitter, VKontakte (ВКонтакте), 4chan, Taobao (淘宝网), Pinterest, Reddit, deviantART, Baidu (百度), New York Times, Lifehacker, Gmail, Google News, Google Search, Bing, Flickr, Wikipedia, etc. Not only this but these extensions are compatible with Google Chrome, Apple Safari, Mozilla Firefox, Opera, Microsoft Edge and Yandex web browsers.
> 
> A few great features in this browser extension:
> ✔ Zoom with a slider
> The best way to zoom perfect in on a web page is to use a slider. You can change the zoom factor from 1 up to 400.
> With one click on the Z toolbar button you see the following buttons:
> • Slider
> • Current zoom value
> • Reset
> • + button to zoom in
> • - button to zoom out
> 
> ✔ Scroll and Zoom
> When you click on the Z button, and scroll up or down with your mouse. Zoom will automatically change LIVE that web page.
> 
> ✔ Zoom all together In/Out
> If you enable this option in the Zoom options page, it will zoom in/out on all the open web pages.
> 
> ✔ Save website Zoom value
> This save automatically the current zoom value of this website. So when you come later back to that website, it restore zoom value since you left the site.
> As user you can always set it back to default zoom, by clicking on the "Reset" button.
> 
> ✔ Zoom Engine
> You as user can choose what zoom engine you want to use. You can use the default browser zoom engine or the CSS website style zoom. That's more smoother and enjoyable.
> 
> ✔ Manage all the Zoom for each website
> • Domain level
> • Web page level
> In the options page you can easily manage, edit or remove the zoom value of that website.
> 
> ✔ Option to display the Zoom value percent number in the Z button as a badge. With the ability to adjust the color to your favorite color.
> 
> ✔ Option to display the context menu better know as the right-click menu with the necessary zoom percentages
> The available menu items are:
> 200%, 175%, 150%, 125%, 100%, 75%, 50%, 25%
> 
> ✔ Option to hold your mouse click and scroll to zoom in or out the current page
> 
> ✔ Option to zoom in or out with your mouse wheel. Hold one of the mouse buttons, left or right. Then simple rotate the mouse wheel to zoom in or out that current web page. You can customize the scroll and hold button in the Zoom Options page.
> 
> ✔ Set default zoom ratio and zoom step
> 
> ✔ Customizable keyboard shortcuts in the browser settings page. This for the following actions:
> • Zoom in on the current web page: ctrl + 1
> • Zoom out on the current web page: ctrl + 2
> • Reset the zoom value for the current web page: ctrl + 0
> 
> ✔ Video and the web
> This is one of the important browser extension also to improve your video entertainment. It zooms in the web page but it increase also the size of the video player example on YouTube™ and HTML5 video. And you can use the most popular Turn Off the Lights extension to dims the part around the video player.
> 
> ✔ An accessibility option to see a larger popup window
> 
> 
> Project Information:
> https://www.stefanvd.net/project/zoom/browser/
> 
> 
> Note: 
> Windows: CTRL and + or CTRL and - 
> Mac: ⌘ and + or CTRL and - 
> Is doing the same action as in this browser extension. But this extension helps you to increase/decrease the zoom to a custom percentage in a better user experience.
> 
> <<< Option feature >>>
> To protect your eyes at night and to get focus on the video player such as YouTube™. It's recommend to use and install the Turn Off the Lights for YouTube and Beyond
> https://chrome.google.com/webstore/detail/bfbmjmiodbnnpllbbbfblcplfjjepjdn

### [Momentum - Chrome Web Store](https://chrome.google.com/webstore/detail/laookkfknpbbblfpciffpaejjkokdgca '0.0')
> 介绍: New Tab page that gives you a moment of calm and inspires you to be more productive. Get inspired with a daily photo and quote, set a daily focus, and track your to-dos. Eliminate distractions and beat procrastination with a reminder of your focus for the day on every new tab. Join over 3 million users and get inspired to create the life you want to live.
> 
> ☆☆☆ Featured in Tim Ferriss’ Tools of Titans, BuzzFeed, TheNextWeb, Lifehacker, Reddit, Product Hunt, Hootsuite, Zapier, and TheDailyMuse! ☆☆☆
> 
> • New inspirational photo and quote each day
> • Set a daily goal/focus/intention
> • Keep track of tasks with Todo list
> • See the weather and forecast
> • Links and search
> • Show bookmarks bar on new tab
> • Default Chrome Tab/Apps links
> • Customize the dashboard by showing/hiding widgets
> • Set your uptime and downtime with Balance mode
> • Feel good and get things done!
> 
> 
> 
> MOMENTUM PLUS
> Unlock added customization, integrations, widgets, and more!
> 
> • Customize font and color themes
> • Add your own quotes and background photos
> • Skip to a new photo or quote whenever you like
> • Todo integrations: Asana, Trello, Todoist, GitHub, Wunderlist, Google Tasks 
> • More widgets: Notes, Countdown timer, Metrics
> • Autofocus mode: pull your tasks into your focus, combine with integrations
> • Enhanced Weather: extra weather info and more accurate feed
> • Enhanced Todo: multi-todo lists and color labels
> • Priority support from our friendly team
> • Support the development of Momentum (Thank you!)
> • Enjoy next level focus and productivity
> 
> 
> ABOUT PERMISSIONS
> 
> Location - Automatic weather setup only
> Yahoo - Weather data only
> 
> We recognize that location sharing is a concern for many people (ourselves included) and it is a responsibility we take very seriously. For more information on privacy and the security of your data visit https://momentumdash.com/privacy.
> 
> 
> HELP & SUGGESTIONS
> Help Center https://momentumdash.help
> Suggestions https://get.momentumdash.help/hc/en-us/community/topics
> 
> 
> GET IN TOUCH
> Email us at help@momentumdash.com
> Blog http://momentumdash.com/blog
> Twitter @momentumdash
> Facebook http://facebook.com/momentumdash
> Instagram http://instagram.com/momentumdash
> 

### [Vim Tips - New Tab Replacement - Chrome Web Store](https://chrome.google.com/webstore/detail/lbhnkgjaoonakhladmcjkemebepeohkn '0.0')
> 介绍: Learn a new vim command every time you open up a new tab.

### [LN2 for Admin - Chrome Web Store](https://chrome.google.com/webstore/detail/lcecnnnnpfldagjjmpjaencpccfafdad '0.0')
> 介绍: With LN2, you can:
> 
> - Detect LAN services within 30 minutes.
> - View and manage all services in one page.
> - Share services with collegues or friends.
> - Recevie notification when services crash.
> 
> Know more about LN2, visit https://ln2.io.

### [QUOTE.fm - Chrome Web Store](https://chrome.google.com/webstore/detail/lckmlcndmcgiemfoninonlmljcmokopk '0.0')
> 介绍: This is the official QUOTE.fm extension.
> 
> QUOTE.fm is the best way to discover, read and share great texts that have the power to convey ideas, provoke emotions or change your entire life. It’s all about texts truly worth reading.
> 
> Find a quality story, mark a spot that sums up the text and makes others want to read it, click the little icon in the upper right corner, write a comment, publish and done. You've recommended a story on QUOTE.fm. 
> 

### [Raindrop.io: "Save Button" for Web - Chrome Web Store](https://chrome.google.com/webstore/detail/ldgfbffkinooeloadekpmfoklnobpien '0.0')
> 介绍: Your bookmarks can be feature-rich, attractive and easy-to-use.
> 
> Collect bookmarks
> Clip articles, photos, videos and pages from web and apps.
> 
> Organize
> Organise bookmarks in collections and tag them. Give each collection a unique look and feel with a custom icon and save bookmarks with a screenshot or cover to find them easily at any time.
> 
> Share & Collaborate
> Work together on collections privately with colleagues, friends and family or make them public and share them with the rest of the world.
> 
> Sync with all devices you use every day.
> You can also import bookmarks from your browser and many other services.

### [Instapaper - Chrome Web Store](https://chrome.google.com/webstore/detail/ldjkgaaoikpmhmkelcgkgacicjfbofhh '0.0')
> 介绍: Instapaper is a simple tool for saving web pages to read later on your iPhone, iPad, Android, computer, or Kindle.
> 
> This browser extension may be used in place of the bookmarklet to save articles directly into your Instapaper queue. 
> 
> It works by saving the current tab to your Instapaper account . Users who aren't logged in will be taken to a login or signup page, after completing the process they will be redirected back to the original page with the original page saved in their queue.

Traceback (most recent call last):
  File "/Users/sqsgalaxys/Downloads/MeProjects/untitled1/pythonGetChromeWebstore.py", line 258, in <module>
### [Error 404 (Not Found)!!1](https://chrome.google.com/webstore/detail/leakmhneaibbdapdoienlkifomjceknl '0.0')
    print("介绍: " + soup.find_all("pre", class_="C-b-p-j-Oa")[0].text)
IndexError: list index out of range

Process finished with exit code 1

### [PlantUML Viewer - Chrome Web Store](https://chrome.google.com/webstore/detail/legbfeljfbjgfifnkmpoajgpgejojooj '0.0')
> 介绍:  PlantUML
> 
> Renders UML diagram as defined in a text file. For full syntax of the text file, see:
> http://plantuml.sourceforge.net/index.html
> 
> 1. Install the extension from Chrome Web Store.
> 2. Check "Allow access to file URLs" in chrome://extensions/.
> 3. Open local or remote text file with UML diagram definition in browser (the text starts with @startuml).
> 4. See the rendered UML diagram!
> 
> If the plugin stops working after update, uncheck and check the "Allow access to file URLs" in chrome://extensions/ again.
> 
> If it does not help, clear the cache (strange Chrome caching behavior). I do not know, what Chrome is doing, but I had to reload background page and popup page of the extension after update.
> 
>  Features
> 
> - Automatically updates the diagram when the local file is changed.
> - You can use your own server by changing the server URL in the popup of the action button (action button is displayed while viewing PlantUML files).
> 
>  Permissions
> 
> Your data on all websites
> :	Used to check whether the current page contains PlantUML diagram.
> 
>  History
> 
> 1.2
> - Added option to change type (PNG/SVG/TXT/None).
> 
> 1.1
> - Recognizes Ditaa and Dot graphs.
> 
> 1.0
> - The first version.
> 
>  Credits
> 
> Credits go to Arnaud Roques, the author of the PlantUML. If you like this plugin, support the original author via the PayPal button on the PlantUML site (http://plantuml.sourceforge.net/index.html).

### [Linkclump - Chrome Web Store](https://chrome.google.com/webstore/detail/lfpjkncokllnfokkgpkobnkbkmelfefj '0.0')
> 介绍: Linkclump gives you the ability to drag a selection box around links using your mouse to quickly open as new tabs, open in new window, save as bookmarks, or copy to clipboard. Similar to Snap Links or Multi Links for Firefox.
> 
> FEATURES
> - Action: choose to open links as new tabs, into a new window, copy to clipboard or saved to your bookmarks. You can setup multiple actions.
> 
> - Activation: choose how to activated the selection box using different mouse and key combinations (including shift/alt/ctrl).
> 
> - Smart Select: tries to select only the important links on the page. Turn off this option to open all selected links.
> 
> - Auto Scroll: the page will automatically scroll up/down to make it easier to select all the links at once.
> 
> - Filter Links: include/exclude links that contain certain words.
> 
> - Delay: set a delay between the opening/closing of each tab.
> 
> - OS Tested: works on windows, mac and linux operating systems.
> 
> Visit https://github.com/benblack86/linkclump to get involved.

### [利器 · 灵感生成器 New Tab - Chrome Web Store](https://chrome.google.com/webstore/detail/lidppokaooioojchghdjekhcgdjkkohe '0.0')
> 介绍: 利器采访优秀的创造者，邀请他们来分享工作时所使用的工具，以及使用工具的方式和原则。进而探索人与工具，人与科技之间的关系。
> 
> 在利器看来，工具可以是一个高效的软件或硬件，也可以是一本书或网站……但凡能辅助创造者完成创造的物件，都是「利器」。这样的工具将赋予更多个体力量，让个体创造出更多可能性。
> 
> 利器 · 灵感生成器 汲取了这些优秀创造者的经典语录，让你在浏览其它网页时总能先驻足停留在新建标签页中，阅读与体会，从这些语录中找寻属于你的利器。
> 
> 灵感生成器地址：http://liqi.io/idea-pump/
> 
> 插件官网：http://staydan.com/#!/product/liqi.newtab
> 
> 反馈问题至：enterzhu@gmail.com
> 
> 更新
> 
> v1.1.6 / 2016.12.28
> 
> - 再次调整数据主动更新间隔
> - 修复造成主动更新数据时偶尔失败的问题
> - 为新用户准备了最新的离线数据，即使没有网络链接也可以使用
> 
> v1.1.5 / 2016.07.11
> 
> - 延长数据主动更新间隔
> - 更正点赞评论的统计代码
> 
> v1.1.3 / 2016.07.09
> 
> - 右侧增加前往Chrome商店评论点赞入口
> - 离线数据更新至2016.06底
> - 提高引言内容格式处理的兼容性
> 
> v1.1.2 / 2016.05.12
> 
> - 改写数据初始化流程，初始数据采用增量更新，提高成功率
> - 加入修复工具和提示指引，仅当新标签页空白时出现
> 
> :) 遇到空白页的用户，若愿意，请联系作者反馈，谢谢
> 
> v1.0.4 / 2016.05.10
> 
> - 调整数据更新机制
> - 增加安装后数据初始化失败时重试次数的限制
> 
> v1.0.0 / 2016.05.04
> 
> - 更新为正式版视觉搞
> - 加入交互
> 
> v0.2.0
> 
> - 重写新建标签页，用最极简的方式呈现灵感生成器中的经典语录
> - 自动更新语录库，让你畅享最新灵感语录
> - 利器官方数据呈现，绝对原汁原味

### [Smart TOC - Chrome Web Store](https://chrome.google.com/webstore/detail/lifgeihcfpkmmlfjbailfpfhbahhibba '0.0')
> 介绍: Display an outline for web page, helpful when you are reading looooong article or docs. 
> 
>  Features:
> 
> - Accurate article/headings detection
> - Displays a (nice-looking) table of contents with sane behavior
> - Only runs when you actually use it
> 
>  Usage:
> 
> - Click browser button to toggle on/off (shortcut: "Ctrl/Cmd+shift+e")
> 
>  Supported sites:
> 
> Any article page that uses HTML heading tags (H1, H2, H3...) properly, examples:
> 
> - Wikipedia.org
> - Github.com
> - npmjs.com
> (...and more)
> 
>  Bug Report
> 
> If it doesn't work correcty for specific site, please open an issue.
> Or report anonymously here: http://notepad.1976f.com/smarttoc_report
> 
> 
>  Recommended by:
> 
> - Appinn.com: http://www.appinn.com/smart-toc-for-chrome/
> 
> 
> 

### [Product Hunt - Chrome Web Store](https://chrome.google.com/webstore/detail/likjafohlgffamccflcidmedfongmkee '0.0')
> 介绍: Product Hunt is a place for product-loving enthusiasts to share and geek out about the latest mobile apps, websites, hardware projects, and technology.  With our shiny new Chrome extension, you can:
> 
>   * View a gallery of the top products of the day in every new tab
>   * Search for products, collections, and people directly from the Chrome menu bar
>   * Open the discussion and product details from the product page itself by clicking the PH Bar
>   * Hunt products and curate collections in a few keystrokes
> 
> Explore more ways to use Product Hunt at http://producthunt.com/apps. 
> 
> Questions, ideas, or just want to say hi? Drop us a line at hello@producthunt.com!

### https://chrome.google.com/webstore/detail/limfkkkgjbcfmfhkclkohdhddfngakhb
https://chrome.google.com/webstore/detail/limfkkkgjbcfmfhkclkohdhddfngakhb

### [Web Maker - Chrome Web Store](https://chrome.google.com/webstore/detail/lkfkkhfhhdkiemehlpkgjeojomhpccnh '0.0')
介绍: A blazing fast web playground that even works offline!

This extension provides you with a very easy accessible and offline playground for your lovely web experiments.
Perfect for developers who want to experiment or practice in HTML/CSS/JS quickly, even without Internet connectivity.

Features:

* Works offline
* Supports preprocessors: HTML (jade, markdown), CSS (SCSS, LESS, Atomic CSS, Stylus) & JavaScript (ES6, CoffeeScript, TypeScript)
* Inbuilt Console
* Save and load your creations with Auto-save
* Fork any creation
* Multi-monitor support with detached preview
* Import & Export all creations anytime, anywhere
* Multiple editor themes & other configurable settings
* Font options + use any system font
* Code autocompletion
* Very easily accessible. Simply open a new tab in Chrome! (configurable setting).
* Multiple layouts with saved collapsed states
* Save as HTML file
* Edit in CodePen
* Preview screenshot capture
* Open source on Github

Lets create!

Permissions Required
* Read URL of the opened page - This is required to give optional new tab replacement feature because Web Maker shows itself only when chrome://newtab is opened

Disclaimer
Web Maker does not track any user specific data. It uses Google Analytics to track aggregated events to improve user experience based on what features are used more. If still you want to opt-out of Google Analytics tracking, please visit http://tools.google.com/dlpage/gaoptout or you can set up a filter in Adblock Plus or similar ad blocker tools like AdBlock, uBlock or Adblock Pro.

Help & Support
Chat - https://gitter.im/web-maker-app/Lobby
Twitter - https://twitter.com/webmakerApp
Website - https://webmakerapp.com

Changelog
v.2.9.5
Improvements in external library ux, pane collapsing and bugfixes

v.2.9.0
Detached preview, Atomic CSS configurations, find/replace, more settings & bugfixes.

v.2.8.0
Auto-save, custom system font, configurable auto-completion, matching tag highlighting, bugfixes and improvements

v.2.7.1
Lots of bug fixes and minor improvements

v.2.7.0
Fork feature, fonts, bugfixes and improvements

v2.6.1
Several bugfixes.

v2.6.0
Inbuilt Console added.!

v2.5.0
search saved items, Atomic CSS support, more configurable settings and bugfixes.

v2.4.3
Whitelist scripts from stripe.com.

v2.4.2
Improved infinite loop protection.

v2.4.0
Import/export, editor themes, more settings, vim keybindings, Add library policy changes.

v2.3.2
Onboarding improvements, does not replace new tabs by default and babel update.

v2.3.0
Preview screenshot capture (new downloads permission required for this), keyboard navigation, auto code alignment & bugfixes.

v2.2.2
Bugfixes in autocompletion

v2.2.0
Code autocompletion, full screen preview, SASS support and bugfixes.
### [Application Launcher for Drive (by Google) - Chrome Web Store](https://chrome.google.com/webstore/detail/lmjegmlicamnimmfhcmpkclmigmmcbeh '0.0')
> 介绍: This extension from Google lets you open Drive files directly from your browser in compatible applications installed on your computer. Start by installing Google Drive for Mac/PC then simply right-click on the file from Google Drive and select “Open with” to see a list of applications on your computer that can open it.
> 
> By installing this extension, you agree to the Google Terms of Service and Privacy Policy at https://www.google.com/intl/en/policies/.

### [Google Keep Chrome Extension - Chrome Web Store](https://chrome.google.com/webstore/detail/lpcaedmchfhocbbapmcbpinfpgnhiddi '0.0')
> 介绍: Found a webpage, image, or quote that you want to save for later? With the Google Keep Chrome Extension, easily save the things  you care about  to Keep and have them synced across all of the platforms that you use — including web, Android, iOS, and Wear. Take notes for additional detail and add labels to quickly categorize your note for later retrieval.
> 
> Features:
>  • Save URLs, text, and images
>  • Take notes on saved content
>  • Add labels to your notes
>  • Automatically saves to Google Keep
> 
> Try Google Keep on the web at http://keep.google.com, on your Android device at http://g.co/keep, and on your iOS device at https://itunes.apple.com/us/app/google-keep-your-thoughts/id1029207872.

### [Extensions Manager (aka Switcher) - Chrome Web Store](https://chrome.google.com/webstore/detail/lpleipinonnoibneeejgjnoeekmbopbc '0.0')
> 介绍: Light popup manager to enable, disable, uninstall extensions, applications quickly and easy. 
> 
> This extension doesn’t handle personal or sensitive user data. 
> https://www.google.com/policies/privacy/
> 
> Please, use http://goo.gl/QAZot for feedback
> 
> 

### [Readhub.Tab - Chrome Web Store](https://chrome.google.com/webstore/detail/lplndfbdjbiofehpnckdkfjobpdbfpma '0.0')
> 介绍: Readhub 第三方浏览器插件，在新标签页显示最新热门文章。

### https://chrome.google.com/webstore/detail/lpppkimladplpkcafniegcicploefkeo
### [Tab Pinner (Keyboard Shortcuts) - Chrome Web Store](https://chrome.google.com/webstore/detail/mbcjcnomlakhkechnbhmfjhnnllpbmlh '0.0')
> 介绍: It's annoying to have to right click a tab and choose "Pin Tab," and slows down your browsing workflow. This extension seeks to solve that by adding in a simple key binding for doing just that: Pinning and Unpinning tabs while browsing.
> 
> The default key binding is Ctrl + Shift + X (or Command + Shift + X on Mac OS X).
> 
> This extension requires no special permissions and doesn't inject anything into a page, the key binding is configurable from your extensions page (at the bottom right of the page there is a "Key Bindings" link) so you can bind this to whatever you feel comfortable typing regularly.
> 
> Once you've got it set up the way you want to get to pinning those tabs quickly and easily!
> 
> ---
> 
> November 27, 2017 Note
> 
> I've uploaded the source for this extension (extremely small) to Github. If you're interested to see what it takes to make this thing tick check out the "tab_pinner.js" file, if you want to make changes just make a PR with your proposed update. Enjoy!
> 
> https://github.com/bbuck/tab-pinner
> 
> ---
> 
> April 30, 2015 Update!
> 
> Due to another comment (I guess another will come shortly after I post this update) there is yet another new command now that allows you to PIN all tabs at once (in the current window). Now you can pin/unpin your current tab and Pin/Unpin all tabs of the current window! Hooray!
> 
> I don't think I'll be willing to add anything more to keep things quite simple; however, if more suggestions do come in and they're not very complex or fit will with what is already done then I will most likely implement them when I can.
> 
> ---
> 
> April 24, 2015 Update!
> 
> Due to comment request (even though it was just one, but I try and take care of you guys) I've added another keyboard shortcut for unpinning all pinned times at once. No other functionality was changed so feel free to use or ignore the new feature!

### [Take Webpage Screenshots Entirely - FireShot - Chrome Web Store](https://chrome.google.com/webstore/detail/mcbpblocgmgfnpjjppndjkmgjaogfceg '0.0')
> 介绍: FireShot takes full web page screenshots. You can edit and annotate captures. 
> 
> You can capture web pages entirely to PDF (with links) / JPEG / PNG files, print, or copy to clipboard. FireShot can work offline.
> 
> * NEW: send screenshots directly to Gmail.
> 
> "The Best Free Google Chrome Extension" by PCMAG.COM.
> 
> The screenshots are instant and produce no traffic. 
> 
> ### What you can do with FireShot:
> 
> ✓ Capture full web pages entirely
> ✓ Capture only visible part of the page
> ✓ Capture selection
> ✓ Save screenshot to disk as PDF (with links), PNG, and JPEG
> ✓ Copy screenshot to clipboard
> ✓ Print screenshot
> 
> ### A FREE upgrade is available. Activate it directly from the menu and:
> 
> ✓ Capture specific elements, such as scrolling areas on web pages
> ✓ Capture all tabs in one click and save to single PDF
> ✓ Edit screenshot: crop, resize, add text and arrow annotations, blur areas and apply other effects
> ✓ Print
> ✓ Save screenshot to PDF files
> ✓ Save captures to disk as PDF, PNG, GIF, JPEG, BMP
> ✓ Send to OneNote (Pro version)
> ✓ Upload to Twitter, Google Picasa, Facebook, ImageShack, Flickr, EasyCaptures
> ✓ Copy screenshot to clipboard
> ✓ Print screenshot
> ✓ E-Mail
> ✓ Export to external editor

### [GayHub - Chrome Web Store](https://chrome.google.com/webstore/detail/mdcffelghikdiafnfodjlgllenhlnejl '0.0')
> 介绍: An awesome chrome extension for github 🐈

### [YouKu HTML5 - Chrome Web Store](https://chrome.google.com/webstore/detail/mdnopkhmebjoaaoicljdmgheecigeobj '0.0')
> 介绍: Play Youku in HTML5

### [Save to Google - Chrome Web Store](https://chrome.google.com/webstore/detail/meoeeoaohbmgbocpdpnjklmfmjjagkkf '0.0')
> 介绍: Easily save interesting webpages to Google with the new Save to Google extension. 
> 
> One-click save: Click the star to save webpages for later viewing. Easily navigate your saves via an intuitive visual UI.  
> 
> One spot for webpages and Images: Your saved webpages and saved images from Google Image Search will live together at google.com/save. 
> 
> Organize your images: Add Tags to organize your saved webpages and images.
>  
> By installing this item, you agree to the Google Terms of Service and Privacy Policy at https://www.google.com/intl/en/policies/.

### [Google Dictionary (by Google) - Chrome Web Store](https://chrome.google.com/webstore/detail/mgijmajocgfcbeboacabfgobmjgjcoja '0.0')
> 介绍: IMPORTANT:
>  - The pop-up bubble will not work in tabs that were open prior to installation. After installing this extension, either reload your open tabs or restart Chrome.
>  - Note that all extensions are disabled on Chrome Web Store pages (including this one). Do not test the extension on this page; it will not work!
>  - If the extension is not working for you, please make sure it's up to date. Visit chrome://extensions/, click the "Update extensions now" button, then restart Chrome.
> 


> With this extension, you can:
> 1) Double-click any word to view its definition in a small pop-up bubble.
> 2) View the complete definition of any word or phrase using the toolbar dictionary.
> 3) Store a history of words you've looked up, so you can practice them later.
> 
> Foreign words are automatically translated to your language of choice.
> 
> Supported dictionaries:
>  - Arabic
>  - Brazilian Portuguese
>  - Chinese (Simplified)
>  - Chinese (Traditional)
>  - Czech
>  - Dutch
>  - English (UK)
>  - English (US)
>  - French
>  - German
>  - Hindi
>  - Italian
>  - Japanese
>  - Korean
>  - Russian
>  - Slovak
>  - Spanish
>  - Turkish
> 
> If you opt in (via the options page), this extension will store a history of all your looked-up words and their definitions. You can download this history as a CSV file at any time. In addition, you can allow other Chrome extensions to access this history. For example, a third-party extension could produce flashcards to help you practice words you've looked up before.
> 
> By installing this extension, you agree to the Terms of Service: https://www.google.com/policies/terms
> 
> Having problems with this extension? If the suggestions above didn't work, please fill out a problem report: https://chrome.google.com/webstore/support/mgijmajocgfcbeboacabfgobmjgjcoja

### [有了！豆瓣阅读Kindle推送服务 - Chrome Web Store](https://chrome.google.com/webstore/detail/miceenljmjllnfcjocahiagkgljpifkl '0.0')
> 介绍: 有了kindle推送服务是一款kindle推送插件
> 目标是方便的推送各种书籍到kindle中
> 更多功能敬请期待

### [Placid Tab New Tab Page - Chrome Web Store](https://chrome.google.com/webstore/detail/mjcblgoejhkkkhgeadejhkpldglnfmcj '0.0')
> 介绍: A minimal New Tab page.
> 
> ** New in V2 **
>  - Now with light AND dark themes!
>  - Options save automatically
> 
> Usage:
> Each quadrant can be assigned to one of your favourite websites. Click a quadrant to navigate to its assigned link.
> 
> Configuration:
> To assign your links, either
>  - Click an unassigned quadrant, or
>  - In the Chrome menu click Tools > Extensions > Placid Tab > Options
> 
> Licence: MIT
> 
> Project page: https://github.com/rileyjshaw/placid-tab

### [MindMap Tab - Chrome Web Store](https://chrome.google.com/webstore/detail/mkgjficalhplaenklhejcbmlkonbakjj '0.0')
> 介绍: This extension provides you with drawing MindMap in Chrome. Each MindMap is stored to your local storage automatically, and you can open the old MindMap diagram quickly.
> 
> Since the version 2.0.0, you can store MindMaps into the Firebase Database. If you are interested in this feature, click the menu "Login" on the header menu (first, you need to create your new account).
> 
> History:
> 
> Dec 27, 2017: Released 2.10.1. Fix the MindMap vertical position problem.
> Dec 27, 2017: Released 2.10.0. Add a new feature to change a font size of the MindMap.
> Dec 25, 2017: Released 2.9.0. Can turn on/off a line color.
> Dec 23, 2017: Released 2.8.0. Add bold/strikethrough text styles.
> Dec 23, 2017: Released 2.7.1. Fix a bug about the history dropdown list.
> Dec 3, 2017: Released 2.7.0. Abolish override a new tab. Instead, provide a browser action.
> Nov 28, 2017: Released 2.6.2. Fix some bugs about calculating a node length.
> Feb 23, 2017: Released 2.6.1. Adjust save timing.
> Feb 20, 2017: Released 2.6.0. Support to move the Canvas with DnD.
> Feb 17, 2017: Released 2.5.0. Support to copy as HTML text.
> Feb 12, 2017: Released 2.4.1. Fix a problem about sync.
> Feb 8, 2017: Released 2.4.0. Support a layout change.
> Feb 7, 2017: Released 2.3.0. Use Ace Editor.
> Feb 6, 2017: Released 2.2.0. When clicking each node, jump to the target position in the textarea.
> Feb 5, 2017: Released 2.1.0. Support exporting MindMap diagram as a PNG/JPEG image.
> Feb 4, 2017: Released 2.0.0. Support Firebase Database.
> 

### [XKCD New Tab - Chrome Web Store](https://chrome.google.com/webstore/detail/mnocgfffoiaibkhagfdfbglooebcengb '0.0')
> 介绍: Turns your new tab page into a random xkcd comic. Source is on Github  at: https://github.com/hackathoner/XKCD-New-Tab

### [Reading Time - Chrome Web Store](https://chrome.google.com/webstore/detail/nccohhimobidpghgpnejnbkpoichbbml '0.0')
> 介绍: A chrome extension that tells you how much time it takes to read a web page article
> 
> update
> - you can close the widget by clicking on it
> 
> description
> - very fast calculation time using firefox readability library
> - does not block rendering of the webpage as it is loaded after everything is done loading on the page
> - works very well on webpage articles
> - does not work well for other types of content
> - can adjust the look of the widget to your liking
> - it's open-source, you can contribute here github.com/usergit/read-time
> 
> privacy policy
> - no data will be collected from this app
> - strong privacy, does not send any of your data to any website
> - no analytics or tracking of any sort

### [Similar Sites - Discover Related Websites - Chrome Web Store](https://chrome.google.com/webstore/detail/necpbmbhhdiplmfhmjicabdeighkndkn '0.0')
> 介绍: Save time searching online with the fastest discovery tool for new websites! 
> 
> Looking for more options than the pages you enjoy when you browse? Trying to find more websites about a topic you’re researching? SimilarSites brings you curated website recommendations for similar pages, intelligently giving you more options.
>  
> Discover and preview similar pages to the ones you visit, instantly! SimilarSites is the #1 extension for discovering new sites you love. While browsing the web, click on the SimilarSites extension to see a list of recommended similar sites to the one you’re currently visiting. 
>  
> SimilarSites works just like Youtube recommendations - showing you relevant websites that are associated with the one you’re already on.
>  
> Get the most out of SimilarSites with the following uses:
>  
> ★★  For Discovery ★★
> This is perfect for discovering new shopping sites, cool blogs and publishers that are offering similar content what you're currently reading, growing your list of inspiring sites and much more!
>  
> ★★  For Marketers ★★
> SimilarSites is an essential marketing tool that allows you to discover competitors you didn’t know about, find leads for your affiliate or media buying campaigns, and discover sites to analyze for keyword research or other growth opportunities.
>  
> ★★  For Sales & Business Development ★★
> SimilarSites is an endless source for lead generation. Any existing lead opens the door to dozens of other leads that fit similar criteria.
>  
> ★★ For Research ★★
> Source more than one website with the leading related content research tool. SimilarSites is the most powerful website affinity engine. Use it for keyword research and to:
> Discover competitors
> Discover sites
> Generate leads
> Explore the web and find more of your favorite content!
>  
> SimilarSites is:
> ✔   Reliable
> ✔   Instant
> ✔   Insightful
>  

 
The technology behind SimilarSites is designed to show that "people who visit this site also like to visit these other related sites". When you download the SimilarSites extension, you join our community of users who contribute anonymized information regarding their browsing experience to improve our site recommendation algorithm. Our community improves our algorithms every minute, ensuring fresh and up-to-date recommendations!

SimilarSites cares very much about your privacy. Usage of the SimilarSites extension requires granting it permission to capture anonymized browsing data. This powers the algorithms that generate information on sites similar to the ones you visit. This data allows us to understand website traffic numbers and flows, which can be used for market research. By installing this extension, you agree to the terms of service and to our privacy policy. For more information, please review our privacy policy before you install our extension, available here: http://www.similarsites.com/privacy-policy

-------------
### [Video Speed Controller - Chrome Web Store](https://chrome.google.com/webstore/detail/nffaoalbilbmmfgbnbgppjihopabppdk '0.0')
> 介绍: HTML5 video provides native APIs to accelerate playback of any video, but most implemented players either hide or limit this functionality. This extension fixes that, plus more... 
> 
> It will help you optimize your video viewing by allowing you to make quick playback speed adjustments, as well as rewind the video to hear the last few second one more time. We don't read at a constant speed, and we talk much slower than we read - there is no reason why we have to listen at a constant speed and at a (very) slow rate.
> 
> Once the extension is installed simply navigate to any page that offers HTML5 video, and you'll see a speed indicator in top left corner of the video player. Hover over the indicator to reveal the controls to accelerate, slowdown, or rewind the video (10 seconds + lowers playback speed). Or, even better, use your keyboard:
> 
> - S - decrease playback speed.
> - D - increase playback speed.
> - R - reset playback speed.
> - Z - rewind video by 10 seconds.
> - X - advance video by 10 seconds.
> - V - show/hide controller.
> 
> If you prefer other shortcuts, want to change the increment value, or want the player to remember your playback speed in the future, head into the settings page and customize it to your heart's content.

### [One-Click Extensions Manager - Chrome Web Store](https://chrome.google.com/webstore/detail/niemebbfnfbjfojajlmnbiikmcpjkkja '0.0')
> 介绍: Notice:This extension used to be named Disable All Extensions Plus(https://chrome.google.com/webstore/detail/ejhdjfmkegkpenillofhpmikailkjpkb).
> But now it has moved to this homepage and Please install this version to update it to a Latest Version(Old version will uninstall automatically in a future time).
> 
> Introduction:Light popup manager to enable or disable, uninstall, update extensions, applications and themes quickly and easy. 
> This extension can help you to Disable all extensions just in one click, and re-enable them also in one click.Also you can enable/disable or uninstall the extensions one by one.
> It's very useful and easy to use.
> version 1.3.3.8 update:
> Remove unessary primacy
> 
> version 1.3.3.5 update:
>   Change the default language to Englisth.
> 
> version 1.3.3.4 update:
>   Remove background process.
> 
> version 1.3.0 update:
>   1.Seperate apps with extension
>   2.Code Refactoring(You may cann't see it.)
>   3.User Interface improved.
> 
> version 1.2.1 update:
>   1.A nice scrollbar
>   2.fixed 2 bugs in logic
>   3.keep it simple, stupid

### [Save to Pocket - Chrome Web Store](https://chrome.google.com/webstore/detail/niloccemoadcdkdjlinkgdfekeahmflj '0.0')
> 介绍: When you find something in Chrome that you want to view later, put it in Pocket. It automatically syncs to your phone, tablet or computer so you can view it at any time, even without an internet connection.
> 
> Extension Features:
> * One-click saving of any page with the toolbar button or keyboard shortcut
> * Right-click menu item to save any link, no need to load the page first
> * Quickly add tags
> * See related recommendations when you save to Pocket
> * Syncs across all devices – iPhone, iPad, Android and more
> * Completely free, upgrade anytime to Premium for a more powerful Pocket experience
> 
> 
> To see trending stories and topics when you open a new tab, get the Pocket New Tab extension:
> https://chrome.google.com/webstore/detail/pocket-new-tab/mlnnopicjonfamklpcdfnbcomdlopmof 
> (Note: Pocket New Tab is only available in the US)

### [List Opened Tabs - Chrome Web Store](https://chrome.google.com/webstore/detail/nkaliaagdnbgadcpnkdbmnigkalbihlb '0.0')
> 介绍: "List Opened Tabs" is a Google Chrome extension that can let you list, search, rearrange, close tabs and switch to another tab.
> It's very useful if you opened a lot of tabs in a window.
> 
> Change log
> v1.0.1: Rearrange Bug fixed

### [ChaZD - Chrome Web Store](https://chrome.google.com/webstore/detail/nkiipedegbhbjmajlhpegcpcaacbfggp '0.0')
> 介绍: 翻译结果和发音朗读由**有道翻译**驱动。
> ChaZD是一款风格简洁，灵巧易用的英汉字典扩展程序，支持英、美两种语言发音，并提供在线划词翻译。
> 
> 注：安装扩展后，请刷新需要查词页面，扩展才会生效！
> 注2:   使用非中文版chrome的用户，如出现弹出窗字体无法正常显示的情况，麻烦请更改浏览器的最小字号为12
>  （具体步骤: settings-->show advanced settings-->Web content中的Customize fonts... -->Minimum font     size将最小字号改为12）
> 
> 主要功能
> 1. 支持在线英汉互译
> 2. 提供英文单词和语句的英音、美音真人发音朗读
> 3. 支持网页内英文划词翻译
> 4. 可通过快捷键（Ctrl+Shift+F）快速启动词典扩展，并可自定义快捷键
> 
> 更新日志
> version 0.8.20
> * 临时版本，解决 API key 封禁问题
> 
> version 0.8.19
> * 修改边栏显示的查词结果被某些网页导航条遮挡的 bug
> 
> version 0.8.18
> * 由于有道的 https 接口连接不稳定，默认改为 http 接口，添加接口的可选项
> 
> version 0.8.16 & 0.8.17
> * 临时版本，优化正则匹配及修复若干潜在 bug
> 
> version 0.8.15
> * 修改 shift 事件没有绑定动态生成元素的 bug
> 
> version 0.8.14
> * 优化查词功能，可解析驼峰命名法、下划词命名法、帕斯卡命名法等词组进行查词
> * 优化带有连字符的词组查询结果
> 
> version 0.8.13
> * 用户可以选择划词发音的类别(英音/美音)
> 
> version 0.8.12
> * 新增划词翻译结果自动隐藏功能
> * 优化设置模块中的显示样式，优化用户体验
> 
> version 0.8.11
> * 修改若干 bug
> 
> version 0.8.10
> * 在输入框输入单词实时响应查询结果
> 
> version 0.8.9
> * 新增划词自动发音功能
> * 接口改用 https 协议
> 
> version 0.8.6
> * 精简了代码量，程序大小减少为原先的一半
> 
> version 0.8.5
> * 增加关闭划词功能按钮
> 
> version 0.8.4
> 1. 优化了长文本的显示
> 2. 查词窗口更简洁
> 3. 同步了划词与弹出窗口的查询结果，想看更详细的翻译结果，划词后直接打开查词窗口就可以啦，还可以配合快捷键使用哦~
> 4. 使用shift键辅助，对之前无法划词的链接进行划词
> 
> version 0.8.3
> 1. 修改若干个BUG
> 2. 新的划词显示窗口
> 3. 划词支持发音功能
> 
> version 0.8.0
> 1. 全新划词显示窗口
> 2. 划词结果新增音标显示
> 3. 针对没有词典翻译，但有网络翻译的词汇在划词中显示结果。
> 4. 划词窗口代码结合jQuery
> 5. 修改划词结果显示字体、行距等bug
> 
> version 0.7.0
> 1. 增加组合键（可选择Ctrl\Command、Alt、Shift）+ 划词的功能
> 2. 优化了词组、短句的翻译结果
> 3. 取消划词结果持续显示时间的设置，改为鼠标点击取消显示，更符合用户的使用习惯
> 4. 浏览器按钮界面显示优化
> 5. 增加通知功能
> 6. 修复一些小BUG
> 
> 项目代码开源在：https://github.com/ververcpp/ChaZD，程序还有待完善，欢迎Clone、使用、提交BUG，并提出您宝贵的意见与建议，非常感谢！

### [RSS Subscription Extension (by Google) - Chrome Web Store](https://chrome.google.com/webstore/detail/nlbjncdgjeocebhnmkbbbdekmmmcbfjd '0.0')
> 介绍: This extension auto-detects RSS feeds on the page you are reading and upon finding one will display an RSS icon in the Omnibox, allowing you to click on it to preview the feed content and subscribe.
> 
> The extension comes with 2 feed readers predefined (Bloglines and My Yahoo) but also allows you to add any web-based feed reader of your choice to the list.
> 
> What's new in version 2.2.2?
>   + Doesn't run in the background all the time, only when in use.
>   + Updated to not use a soon-to-be-deprecated API.
> 
> What's new in version 2.2.1?
>   + Removed Google Reader and iGoogle from the list of default feed readers.
> 
> What's new in version 2.1?
>   + This extension is now available in over 40 languages.
>   + If you see localization problems, let us know: http://crbug.com/37233 
> 
> Changelist:
>   + Navigating to feed pages directly now takes you to the subscription page (instead of showing XML).
>   + Found a feed where this doesn't happen? Let us know: http://crbug.com/32967
>   + Added an Options page for configuring feed readers.
>   + Added an option to skip the feed preview page when subscribing.
>   + Added a link to the preview page for those wanting to copy the direct feed link (look for the [ Feed ] link in the blue bar).
>   + Added support for multiple feeds per page.
>   + When will this be added to Chrome? Star this bug: http://crbug.com/33181 to keep track.

### https://chrome.google.com/webstore/detail/nmmhkkegccagdldgiimedpiccmgmieda

### [Fatkun Batch Download Image - Chrome Web Store](https://chrome.google.com/webstore/detail/nnjjahlikiabnchcpehcpkdeckfgnohf '0.0')
> 介绍: Just one click to download all images which selected on the pages. 
> 
> Can use your own rules to download images list.
> 
> Can batch rename downloaded images.

### [HPP Finder - Chrome Web Store](https://chrome.google.com/webstore/detail/nogojgcobcolombicplhimbbakkcmhio '0.0')
> 介绍: HTTP Parameter Pollution (HPP) is a recently discovered web exploitation technique. Please read the NDSS 2010 paper for more details about the technique. HPP Finder is a Chrome extension designed for detecting HPP attempts. HPP Finder can detect URLs and HTML forms that might be susceptible of parameter pollution, but it is not a complete solution against HPP. 
> 
> See example at: http://www.ics.forth.gr/~elathan/extra/hpp/index.html

### [Personal Blocklist (by Google) - Chrome Web Store](https://chrome.google.com/webstore/detail/nolijncfnkgaikbjbdaogikpmpbdcdef '0.0')
> 介绍: The personal blocklist extension will transmit to Google the patterns that you choose to block. When you choose to block or unblock a pattern, the extension will also transmit to Google the URL of the web page on which the blocked or unblocked search results are displayed. You agree that Google may freely use this information to improve our products and services.
> 
> By installing this extension, you agree to the Terms of Service at https://chrome.google.com/extensions/intl/en/gallery_tos.html
> 
> The icon used was created by mouserunner.com under Creative Commons License (http://creativecommons.org/licenses/by-sa/2.5/), thanks!
> 
> Tip: Hide the browser button by right-clicking on it and selecting "Hide button".
> 
> New features in version 1.4:
> - import a list of patterns
> - plain text pattern list for export
> - block host of currently active tab
> 
> New feature in version 2.1:
> - export the blocklist to your Google account
> 
> Bug fix in version 2.3:
> - support for international Google domains on https
> 
> Bug fix in version 2.4:
> - block links are added in new line to avoid dynamic line-breaks
> 
> Bug fix in version 2.5:
> - fixed an issue with overlapping link display on the search results page
> 
> Bug fix in version 2.6:
> - fixed an issue with the extension not being triggered for some search urls
> 

### [Link Revealer - Chrome Web Store](https://chrome.google.com/webstore/detail/nphhadgebjlmcfleikmiedhohdfbfoin '0.0')
> 介绍: This extension will show up the url of the link you're going to click.
> 
> You are probably asking yourself why this extenions was made for...well this, believe it or not, were made because modern browsers like Google Chrome are going to hide at the most the status bar of the url you're going to click. So i hope with this that you're going to know more where are you going to surf to.
> But this extensions will not end up here, we're going (yes, this is not only my idea) to add some more nice features, so don't forget to come visit this page.
> Thanks for trying, as always comments or suggestions are appreciated :)
> 
> CHANGELOG:
>  - 0.3: Add support for target=_blank links. Updated libs and more.
>  - 0.2.2: the tooltip was not shown correctly on mouseover.
>  - 0.2.1: updated to work with latest versions of Chrome
>  - 0.2.x: more to come :)
>  - 0.2: As promised here's the first update with some new nice features like:
>          - Now you can set the tooltip to be viewed also as a statusbar (with configurable position) or keep it as a simple tooltip
>          - Added a timeout to the tooltip to be shown
>          - First SEO Tool: Domain Highlighter (to understand better if you're are going to surf into the same website or not).
>  - 0.1: First initial version. Links are shown up on mouseover.
> 
> SOURCE-CODE:
> https://github.com/julianxhokaxhiu/chrome-link-revealer
> 
> THANKS TO:
>  - Simone Righini, http://www.goatseo.com, The inventor of the idea
>  - Luca Conti, http://www.patonza.net, Support for some next features that will come
> 

### [Get opened tabs URLs - Chrome Web Store](https://chrome.google.com/webstore/detail/npmcbpbplngfameipiobaemkcpnaiiic '0.0')
> 介绍: Sometimes you want to copy all the opened links to the clipboard to reuse them out of the browser. If you only want that feature, and not a tab menu or a session manager, this extension will fit.
> 
> Changelog:
> * v0.2: really copy to clipboard instead of select all

### [Review Bookmarks - Chrome Web Store](https://chrome.google.com/webstore/detail/oacajkekkegmjcnccaeijghfodogjnom '0.0')
> 介绍: This tool can help you review your bookmarks. 
> Maybe we'll find some new ideas from these old bookmarks.
> Maybe some out-of-date bookmarks need to be deleted.
> Whatever purpose for you, I wish you have a good  time on this tool.
> 
> 
> If you think this is a useful tool , please donate me. 
> http://www.domyself.me/donate
> 
> 
> 温故知新 这个插件是用来帮助你重新阅读你那些N久之前存储的书签的工具。
> 也许我们会从这些老旧的书签中发现新的想法，
> 也许一些过时的书签我们应该删掉他了。
> 无论目的如何，我都希望大家能使用愉快~
> 
> 如果你觉得这个工具很赞，欢迎捐助：
> http://www.domyself.me/donate

### [Lookmark - Chrome Web Store](https://chrome.google.com/webstore/detail/oafagjdanmmmmndmikaehdpamligdaeo '0.0')
> 介绍: You need Lookmark for iOS to receive lookmarks from Chrome. Download from http://lookmark.io/download.
> 
> Please send us your feedback at feedback@lookmark.io.
> 
> - The Lookmark Team

### [Adblock Pro - Chrome Web Store](https://chrome.google.com/webstore/detail/ocifcklkibdehekfnmflempfgjhbedch '0.0')
> 介绍: reliable AdBlock engine with a superfast blocking engine and the goal to block 100% of ads on Websites, Youtube, Facebook and many more.
> 
> FEATURES
> - blocks all ads on all websites
> - blocks youtube video and preroll ads
> - Malware and Tracking

### [单词小卡片: 查词/收集/背单词 - Chrome Web Store](https://chrome.google.com/webstore/detail/oegblnjiajbfeegijlnblepdodmnddbk '0.0')
> 介绍: 建议大家与 Steward扩展 一同使用背单词
> 
> update:
> v2.2.6
> 点一个释义就删除;
> ctrl + 鼠标选中弹出查词;
> 部分情况下的iframe 兼容处理
> 
> 
> 近期更新：
> 单词库容量限制与提醒；
> 兼容 简悦 类阅读器
> 
> feature:
> 取词翻译，自动收集单词
> 单词管理

### [Checker Plus for Gmail™ - Chrome Web Store](https://chrome.google.com/webstore/detail/oeopbcgkkoapgobdbedcemjljbihmemj '0.0')
> 介绍: • The fastest and easiest way to manage multiple email accounts
> • 5 star extension with great reviews!
> • Trusted developer of many extensions
> • 1 million satisfied users worldwide
> • Lots of features, options and updates
> • Extensive FAQs and personal tech support with very quick responses
> • Safer. Requires minimal permissions.
> • Can be used as an FVD Speed Dial widget
> Click "Website" or visit jasonsavard.com for more info.
> 
> • Extra features are available upon contributing "any" amount.
> 
> • Supports Push Notifications
> 
> • Supports Inbox by Gmail
> 
> • Beautiful Material Design
> 
> • I'll add your suggestions
> 
> • See the people emailing you just like in the Gmail chat notification, with an option to show their contact photos or your assigned photos for them.
> 
> • Voice notification: If you get an email while you're busy watching a movie or cooking dinner this extension can optionally read it out loud ie. "Jason says, dinner at my place". It's great for the visually impaired.
> 
> • Option to monitor any Gmail or custom labels
> 
> • Option to run in this notifier in the background when Google Chrome is closed and still get new email alerts
> 
> • Popup mail preview window to read, archive, mark as read or delete emails without leaving the current tab (or option to go directly to your Gmail tab)
> 
> • Supports offline view
> 
> • Can also be used as a widget for the extension "Awesome New Tab Page" (ANTP) which supports multiple accounts
> 
> • Desktop sound or voice notifications when new mail arrives or add your own sounds
> 
> • Support for multiple Gmail and Google Apps accounts
> 
> • Add voices
> 
> Changelog: https://jasonsavard.com/wiki/Checker_Plus_for_Gmail_changelog

### [Motivation - Chrome Web Store](https://chrome.google.com/webstore/detail/ofdgfpchbidcgncgfpdlpclnpaemakoj '0.0')
> 介绍: Replaces your 'new-tab' page with a real-time counter showing your current age.

### [JetBrains Toolbox Extension - Chrome Web Store](https://chrome.google.com/webstore/detail/offnedcbhjldheanlbojaefbfbllddna '0.0')
> 介绍: JetBrains Toolbox App should be installed on your computer to make the extension work. Download JetBrains Toolbox App from here https://www.jetbrains.com/toolbox/app/

### [Modern New Tab Page - Chrome Web Store](https://chrome.google.com/webstore/detail/ogllliimbhgmclkgjldeffhjbhaenapo '0.0')
> 介绍: Modern New Tab Page is highly customizable. You can modify the background image, opacity and color. Tiles can also change colors an icons. You have 26 color themes to choose or you can make your own theme if you want to.
> 
> You can change each tile's color, icon, size and even display the latest news of your favorite websites by using RSS. All in one simple and easily configurated page. 
> 

If you have any question, feature request or bug to report, please use the "Send Feedback" button located on the right of the details pane so I can reply to you. I can't reply on the reviews section. Thanks!


Features:

- Create and edit tiles.
- Change the background and font colors, display name, and icon of each tile.
- Upload tile's icon from your computer or select an icon from a list of famous website icons or use a link to use any image on the internet.
- Display the latest news of your favorite web sites by using RSS.
- Click on any news to open it.
- Drag and drop to organize the tiles the way you like.
- Change the tiles' size to fit more tiles on the screens or to display larger tiles.
- 26 color themes ready for you to personalize your page.
- Make your own color theme using color pickers.
- Upload your favorite image to use as background.
- Change the background image opacity.
- View and reopen your recently closed tabs.
- View and open your bookmarks.
- Export and import your tiles and configurations *new


This extension will ask for the following permissions:

- Read and change your bookmarks
  This is required to get the list of your bookmarks so we can add the shortcuts.

- Read and change your navigation history
  This is required to read your navigation history so we can add the shortcuts to your recently closed tabs.

- Management 
  This is required to get a list of your installed apps so we can add the shortcuts.

- Access to all websites
  This permission allows the extension to make requests to external servers. This is necessary to download RSS files and display the last news on your tiles.
  No information is collected.


### [Chrome Apps & Extensions Developer Tool - Chrome Web Store](https://chrome.google.com/webstore/detail/ohmmkhmmmpcnpikjeljgnaoabkaalbgc '0.0')
> 介绍: The Chrome Apps Developer Tool helps developers build and debug Chrome Apps and Extensions. 
> 
> The features include:
> - Separate view for unpacked apps/extensions
> - Inspect views for inspecting app/extension pages using dev tools
> - Reload an app/extension
> - Launch an app/extension
> - View permissions
> - Pack an app/extension
> - Uninstall an app/extension
> - Load an unpacked app/extension
> - Search for app/extension
> 
> By installing this item, you agree to the Google Terms of Service and Privacy Policy at https://www.google.com/intl/en/policies/.
> 

### [Mercury Reader - Chrome Web Store](https://chrome.google.com/webstore/detail/oknpjjbmpnndlpmnhmekjpocelpnlfdi '0.0')
> 介绍: The Mercury Reader extension for Chrome removes ads and distractions, leaving only text and images for a clean and consistent reading view on every site.
> 
> Features:
>  - Disable surrounding webpage noise and clutter with one click
>  - Send To Kindle functionality
>  - Adjust typeface and text size, and toggle between light or dark themes
>  - Quick keyboard shortcut (Cmd + Esc for Mac users, Alt + ` for Windows users) to switch to Reader on any article page
>  - Printing optimization
>  - Sharing through Facebook, Twitter and Email
> 
> Version 4.2.4.0 includes:
>  - bug fixes
> 
> Note to Readability users: if you've been a happy Readability extension user, we think you'll love the new Mercury Reader! Mercury Reader has the best features of Readability like a clutter-free reading experience, customizable themes, and even Send to Kindle, but it's a whole lot faster and is powered by the all new Mercury Parser for more consistently clean web pages.

### [煎蛋妹子图小助手 - Chrome Web Store](https://chrome.google.com/webstore/detail/onchcnnpkgcdjmlcfhkodmkbnfpknodh '0.0')
> 介绍: 煎蛋妹子图小助手
> 
> 用更方便的方法浏览煎蛋妹子图（http://jandan.net/ooxx）
> 
> 功能：
> 1. 图片更新提示
> 2. 自由改变浏览图片的大小
> 3. 一次加载更多的图片
> 4. 自动播放
> 5. Vote
> 
> v1.2.0
> fixed gif images url problem
> v1.1.9
> fixed image loading problem
> v1.1.8
> fixed the issue that the image won't load
> v1.1.4
> notify when new pics are detected
> v1.0.3
> fixed to allow play gif
> 
> 联系作者: lxian2shell@gmail.com

### [word highlight - Chrome Web Store](https://chrome.google.com/webstore/detail/ooabkmkhabkahcjbgpiajffckeibpdoa '0.0')
> 介绍: keywords highlight for Google Search and All

### [Mosh - Chrome Web Store](https://chrome.google.com/webstore/detail/ooiklbnjmhbcgemelgfhaeaocllobloj '0.0')
> 介绍: Install Mosh on your remote server (http://mosh.mit.edu) to use this app. Mosh for Chrome is especially useful for Chrome OS users.
> 
> Mosh provides a remote terminal session similar to ssh, but is tolerant of network issues such as latency, disconnections, and moving from one network to another. You can leave Mosh running all the time, even while your laptop is in standby, and expect your session to persist.
> 
> See the upstream Mosh project at http://mosh.mit.edu for more details.

### [Proxy SwitchyOmega - Chrome Web Store](https://chrome.google.com/webstore/detail/padekgcemlokbadohgkifijomclgjgif '0.0')
> 介绍: Changing proxy settings has never been so convenient. Think SwitchyOmega as a modern version of the "Proxy Settings" dialog, designed to be simpler, quicker and more powerful, specially optimized for Chrome.
> 
> No more digging through the advanced section in Chrome settings. No repeated filling and clearing the proxy config dialog of your operating system. Just tell SwitchyOmega about all your proxies, and enjoy switching with one click on the popup menu. You can also teach Auto Switch to use the right proxy for the right website automatically.
> 
> NOTE: Please report issues by RIGHT-clicking the extension icon and select the "Report Issue" in the context menu so that I can locate and fix the issue more quickly.
> 
> Alternative download link (Github): https://github.com/FelisCatus/SwitchyOmega/releases
> 
> SwitchyOmega is absolutely free and open source. It does not insert ads into any website. It contains absolutely no malware. It just does proxy configuration, and aims to be perfect tool of that.
> 
> Disclaimer: SwitchyOmega does not come with any proxy server, VPNs or anything like that. Thus, SwitchyOmega will not magically unblock websites or protect your privacy, unless you instruct it to use a proxy server which does. You should only use trusted proxy servers, because SwitchyOmega can not protect you from bad proxies that inject ads, track you or record your password. And if you don't have a proxy server, you probably won't need SwitchyOmega. Sounds reasonable, right?
> 
> Privacy Policy: https://github.com/FelisCatus/SwitchyOmega/wiki/Privacy#english
> 
> The 2.x version features:
> * HTTP/HTTPS proxy authentication (username & password) is now supported.
> * More flexible proxy configurations: Fixed servers, multiple SwitchProfile and rule lists.
> * Reviewing and modifying proxy settings for resources that fail to load.
> * New types of condition for switching and improvements to the existing condition types.
> * Optimized performance for both PAC script generating and switching.
> * Improved user experience in options page and dropdown menu.
> * Many Bug fixes and improvements. More testing.
> 
> == Translations ==
> You can help improve the translation of SwitchyOmega or translate it into your language on Weblate:
> https://hosted.weblate.org/engage/switchyomega/?utm_source=widget
> 
> == Upgrading from SwitchySharp ==
> 
> SwitchyOmega will try to use the existing SwitchySharp options (if installed) on installation. All options will be updated, and you can enjoy the new features without having to redo your configuration. If things don't work automatically for you, you can export a backup file manually in SwitchySharp and then import the file in SwitchyOmega.
> 
> CONFLICTS: SwitchyOmega will conflict with other extensions trying to control the proxy settings. Such conflicts are caused by the design of the Chrome browser and thus cannot be avoided. When SwitchyOmega has a higher priority, it can be configured to voluntarily give back the control by selecting the [System Proxy] item in the popup menu. Otherwise, you will see a red badge on the SwitchyOmega icon indicating insufficient priority. Re-installing SwitchyOmega should raise its priority, providing a possible workaround.

### https://chrome.google.com/webstore/detail/padhohbdomknelobmiphhcafepnfipaa
### [為什麼你們就是不能加個空格呢？ - Chrome Web Store](https://chrome.google.com/webstore/detail/paphcfdffjnbcgkokihcdjliihicmbpd '0.0')
> 介绍: 如果你跟我一樣，每次看到網頁上的中文字和英文、數字、符號擠在一塊，就會坐立難安，忍不住想在它們之間加個空格。這個 Google Chrome 的外掛正是你在網路世界走跳所需要的東西，它會自動替你在網頁中所有的中文字和半形的英文、數字、符號之間插入空白。
> 
> 漢學家稱這個空白字元為「盤古之白」，因為它劈開了全形字和半形字之間的混沌。另有研究顯示，打字的時候不喜歡在中文和英文之間加空格的人，感情路都走得很辛苦，有七成的比例會在 34 歲的時候跟自己不愛的人結婚，而其餘三成的人最後只能把遺產留給自己的貓。畢竟愛情跟書寫都需要適時地留白。
> 
> 與大家共勉之。
> 
> Fork me on GitHub:
> https://github.com/vinta/pangu.js
> 
> 版本訊息：
> 
> v3.3.0
> - 修個 bug 好過年
> - 修正在 Twitter 上跟 Buffer 一起使用時會隨機出現的錯誤問題
> 
> v3.2.1
> - 又他媽改善效能問題
> 
> v3.2.0
> - 修正效能問題
> 
> v3.1.1
> - 剛吃完烤肉來改進一下 Paranoid Text Spacing 演算法
> 
> v3.1.0
> - NodePangu 新增 spacingFile()，支援 callback 與 promise
> - NodePangu 新增 spacingFileSync()
> 
> v3.0.0
> - Isomorphic!
> 
> v2.5.6
> - 大家好，很抱歉這麼快又跟大家見面了
> 
> v2.5.5
> - 持續改進 Paranoid Text Spacing 演算法
> 
> v2.5.1
> - 再次改進 Paranoid Text Spacing 演算法
> 
> v2.5.0
> - 改進 Paranoid Text Spacing 演算法
> 
> v2.4.2
> - 修正 Facebook 留言框的空格錯位
> 
> v2.4.1
> - 修正 <title> 網頁標題的加空格
> - 修正 ' 單引號的加空格
> 
> v2.4.0
> - 改善效能
> - 完善對雙引號的處理
> - 修正 Popup Page 的 css 問題
> 
> v2.3.4
> - 再度完善 Paranoid Text Spacing 演算法
> - 修正 Options Page 的小錯誤
> 
> v2.3.3
> - 完善 Paranoid Text Spacing 演算法
> 
> v2.3.2
> - 心血來潮，加個版本號！
> 
> v2.3.1
> - 真的不會對 <code> 和 <pre> 裡的文字加空格了
> 
> v2.3.0
> - 威力加強版！
> - 解決特定情況下在同一個地方會一直加空格的問題
> 
> v2.2.3
> - 不會在 Google+ 的輸入框裡加空格
> - 記事本不懂 Vim 的黑
> 
> v2.2.2
> - 我忘了這個版本到底更新了什麼了......
> 
> v2.2.1
> - 改進 Paranoid Text Spacing 演算法
> 
> v2.1.2
> - 不會對 <textarea> 裡的文字加空格！
> 
> v2.1.1
> - 不對 _ 加空格
> - 對 | 加空格
> - 新增 Popup Page
> - 空格之神 姍姍來遲
> 
> v2.1.0
> - 解決在 Facebook、Twitter、QQ 空间、百度贴吧等網站輸入文字時游標會亂衝的問題
> - 支援 file:/// 開頭的檔案
> 
> v2.0.2
> - 遇到 br 不加空格
> 
> v2.0.1
> - 拿掉 console.log()
> 
> v2.0.0
> - 新年新氣象，全新 UI 和 Icon
> - 網址黑白名單使用 Chrome 的同步功能
> - 修正在 Gmail 中加空格的問題
> - 改善效率問題
> 
> v1.8.0
> - 修正在 Google Docs 中游標錯位的問題
> - 網址黑、白名單支援 // 前綴

### [Live Reload - Chrome Web Store](https://chrome.google.com/webstore/detail/pccddenngcbofbojodpghgpbheckgddn '0.0')
> 介绍: Live Reload 介绍：
> ======================
> Live Reload 是一个旨在提高web前端开发者开发效率的chrome扩展。它可以在你编辑页面资源（html,js,css）的时候，自动获取最新的文件并重新载入，避免开发过程需要频繁按 F5 页面的烦恼。特别适合在双屏环境下进行 web 前端开发，使你不必在编辑器和浏览器之间不停的切换，提高工作效率。
> 
> 特性:

* 只需要安装一个 chrome 插件，不需要特殊的服务器端支持
* 启用实时更新模式后，能够自动重新载入 html/js/css 等资源更新
* 不启用实时更新模式，也能够通过按 F9 来手动重新载入 css 文件
* 支持本域和跨域资源的实时更新，可以通过配置项只监控本域资源更新
* 支持重新载入页面的时候，保留页面滚动条位置
* 页面的资源支持相对路径，绝对路径
* 可以通过 F8 来启用【显示页面节点 id,class 信息】功能，便于开发过程中在编辑器快速定位
* 提供启用Live Reload的页面管理界面
* 能够通过配置选择监控的资源类型和频率

配置项说明：
----------------------
* 启用 Live Reload 的资源类型【css/js/html】：可以选择只实时更新某一类型的资源
* 保持滚动条位置：重新载入页面的保留滚动条位置
* F8显示 Dom#Id.Class ：在实时模式/手动模式下，都可以通过按 F8 来显示页面节点 id 和 class 信息
* F9刷新 CSS：是否启动按 F9 手动载入 CSS 更新
* 只监控本站点资源：是否忽略非本域资源，只监控本域资源更新
* 刷新频率：定时从服务器更新资源的频率

暂不支持:
----------------------
* 由于 chrome 安全机制，暂不支持通过 file:// 打开的页面
* 不支持页面中的 iframe 内资源的变化
* 无法监控 CSS 中使用 import 引入其它 CSS 的情况

使用方法:
---------------------
* 先安装 Live Reload 扩展，可以通过 chrome store 安装，也可以下载后拖入浏览器手动安装
* 安装后扩展栏会出现一个 Live Reload 图标
* 把正在开发的页面资源部署一个 Web 服务器上
    * 可以选择在本机架构 Apache/Nginx/IIS/Tomcat 等专业服务器
    * 如有 Python 运行环境，可以通过在页面根目录执行 python -m SimpleHTTPServer 8999 快速架构服务器
    * 可以选择配合 Fiddler/Rythem 等本地替换工具进行开发
* 在 chrome 地址栏内输入页面地址，可以通过点击 Live Reload 图标，来启用实时监控模式
* 在你最喜欢的编辑器中修改页面资源内容后，可以看到页面上已经更新
* 可以再次点击 Live Reload 图标，图标变灰，不启用实时监控模式
* 可以通过按 F8 来启用/隐藏(F8/ESC)【显示页面节点 id,class 信息】功能，便于开发过程中在编辑器快速定位
* 可以通过按 F9 来手动更新页面 CSS 资源
* 可以在 Live Reload 图标右击，选择选项，可以在配置页面上面设置相关参数
* 设备允许的情况下，推荐使用双显示器进行工作，将 chrome 放在副屏幕，代码编辑器在主屏幕，编辑后可以预览效果
* 设备不允许，可以选择使用小工具将 chrome 窗口置顶或者将编辑器和 chrome 窗口进行左右分栏


-------------
### [Tab Memory Saver - Chrome Web Store](https://chrome.google.com/webstore/detail/pehgadfgejpbgkgkofomjkbgfbnhdfll '0.0')
> 介绍: Full code is available under: https://github.com/KyongTsu/TabMemorySaver
> 
> Now with Settings Sync.
> 
> Chrome can take a good amount of memory of your personal computer when you have opend a lot of tabs.
> These tabs take memory, that is need for other task and these unused tabs can slow down your computer.
> 
> Tab Memory Saver suspends tabs after a specific amount of time (standard is 1 hour) and you can unsuspend this tab later again.
> A suspended tab doesn't use any memory, becaue chrome doesn't have to keep the html, images, javascript and many things more in the memory.
> 
> We try to improve this extension over time, some things like pdf suspension or flash files don't work as expected or wished by us. Keep tuned
> We will inform you about updates and new features.
> 
> This extension is not affiliated or related an in any way to other extension that do the same thing or Google. Its and independent extension with an independent developer (me).
> Some parts are used under GPL which are stated in the source code files.
> Thanks.

### [Multi-highlight - Chrome Web Store](https://chrome.google.com/webstore/detail/pfgfgjlejbbpfmcfjhdmikihihddeeji '0.0')
> 介绍: Can do for you:
>  - Highlight multiple english words on all pages. (whole word matching for english words, currently)
>  - Your words will be saved.
> 
> * Needs to refresh opened pages after install this extension.
> 
> 
> If you love it, you can support it on Patreon (https://www.patreon.com/alexius_lee) or donate via PayPal (https://www.paypal.me/alexiuslee)
> 
> 
> Change log:
>  - 1.12~1.20 - Bug fix.
>  - 1.11 - Temporary rollback to v1.7.
>  - 1.10 - Change: Skip "content editable" elements; Support single letter non-english words.
>  - 1.7~1.9 - Bug fix.
>  - 1.6 - Can do highlighting after first installed, without refresh page.
>  - 1.5 - Fix some bugs, better description.
>  - 1.4 - Add a switch button, to enable or disable highlighting.
>  - 1.3 - HTTPs page enable, redesign highlight logic.
>  - 1.2 - Icon beautify, fix some bugs.
>  - 1.1 - Highlight style beautify.
>  - 1.0 - Core function complete.

### [TransIt - Chrome Web Store](https://chrome.google.com/webstore/detail/pfjipfdmbpbkcadkdpmacdcefoohagdc '0.0')
> 介绍: # TransIt
> 
> TransIt - 让划词翻译更简单
> 
> http://gdgxian.org/crx-transit/
> 
> ## 功能列表
> 
> - 页面英文划词翻译 
> - 连续对多个单词进行划词翻译
> - 对超链接中的文本进行划词翻译
> - 调整页面划词翻译结果显示的时间长短
> - 适应更多的页面，包括 Iframe 嵌套
> - 支持在窗口边缘和选词附近两种方式显示翻译结果
> - 支持百度和有道翻译两种翻译服务
> 
> ## 相关资源
> 
> - 更新历史 http://git.io/pz7B
> - 项目主页 http://git.io/pz7K
> - 问题和反馈 http://git.io/pz7M

### [Data Saver - Chrome Web Store](https://chrome.google.com/webstore/detail/pfmgfdlgomnbgkofeojodiodmgpgmkac '0.0')
> 介绍: Reduces data usage by using Google servers to optimize pages you visit.
> 
> Browse more for less!
> 
>   By enabling this extension, Chrome will use Google servers to compress pages you visit before downloading them. Pages accessed using private connections (HTTPS) or in incognito tabs will not be optimized or seen by Google. Get more visibility into your data usage by clicking on “Details” to see how much data is used by the sites you visit. This might help you make more informed decisions regarding your usage based on the type of connection you are using.   
> 
> You can also enable Data Saver on Mobile Chrome on Android from the Settings menu.
> 
> Learn more about Chrome’s Data Saver at https://support.google.com/chrome/?p=data_saver_off
> 
>   By installing this extension, you agree to the Google Terms of Service and Privacy Policy at https://www.google.com/intl/en/policies.

### [Link Bucket - Chrome Web Store](https://chrome.google.com/webstore/detail/pgmdegekealdadalnoijnglabminmoil '0.0')
> 介绍: * Don't need an account.
> * Anonymous
> * Automatic Synchronization
> * Export (HTML & JSON) 
> 
> 
> LinkBuckets:
> http://linkbuckets.com
> 
> Bug?
> dev@linkbuckets.com
> 

### [Context Menus - Chrome Web Store](https://chrome.google.com/webstore/detail/phlfmkfpmphogkomddckmggcfpmfchpn '0.0')
> 介绍: The extension is simple and does not have any fancy things, users select the text after the right button to display the search menu or the right picture display image search.
> 
> The major search engines include: Google, Baidu, Taobao and television cartoon, University Library, material software and each big mall.
> 
> The expansion of a two-dimensional code generation and recognition function, if the identification of two-dimensional code is address is automatically opened.
> 
> Goo.gl short URL is supported.
> 
> Goo.gl short URLs adds support. Support for custom searches, combined search and custom combinatorial search.
> 
> New user interface, cloud storage settings, super drag, custom menus shared blacklist.
> 
> Customizing tips:%s selected text or pages or links,%g converted into GBK character set,%t into BIG5 character set,%p clipboard contents,%u current page name
> 
> 4.1.314
> Fix LinkMenu i disable all options bug
> Fix %g bug
> 
> 4.1.313
> Notification and fix bug
> 
> 4.1.312
> settings bug
> 
> 4.1.311
> Cloud storage and get menu
> 
> 4.1.310
> Increased set of export functions
> 
> 4.1.308
> Increase Context Menus Mate 
> https://chrome.google.com/webstore/detail/gojgagdabkhlnoeglbklbcebanlfnjkl 
> Enhanced Super Drag and Drop
> 
> 4.1.305
> Because the new policy extensions google single principle, cancel super drag and drop functionality
> 
> 4.1.304 
> Increase Bitcoin pictures 
> Close button design modifications 
> Server Pages adjustment 
> 
> 4.1.303 
> Rename bug fixes 
> Taiwan youtube name bug fixes
> 
> 4.1
> 
> 4.1.302 
> Increase in chrome appcache 
> fix menu increased error
> 
> 4.1.301 
> analytics votive 
> Super Drag and Drop repair
> 
> 4.1.300 
> Important Upgrade 
> Open source software to github.com 
> ui framework upgrade 
> Abandon Web SQL Database 
> A large number of bug fixes
> 
> 3.1.296
> Short URL fault repair
> 
> 3.1.291
> close tab.
> 
> 3.1.289
> Enter search
> 
> 3.1.288
> Drag and drop text link error correction variable
> Input box prop turn Error Correction
> 
> 3.1.287
> Increase short links t.cn, url.cn, dwz.cn
> 
> 3.1.286
> Russian support
> 
> 3.1.284
> Initialization Exception correction
> Pop-up window button names display correctly
> 
> 3.1.278
> Custom Menu Sharing
> Blacklist
> Automatic Update
> Rename
> Language icon can be hidden
> Modify button to hide the menu
> 
> 3.1.274
> update jd.com
> 
> 3.1.272
> Changing Cloud Storage
> 
> 3.0.270
> Add Baidu map
> 
> 3.0.269
> Drag the text is a URL then automatically open
> 
> 3.0.267
> Clipboard access
> 
> 3.0.266
> Zoned word drag up and down around the table to support open
> 
> 3.0.265
> QQ space to increase the share
> 
> 3.0.264
> Modify GBK and BIG5 encoding conversion library
> Add watercress movies, books watercress
> 
> 3.0.262
> Increase W3Chtml, css validation, modification iqdb title
> 
> 3.0.260
> Han Dian update, add thepiratebay
> 
> 3.0.259
> Increase Precautions
> QR code generates an error correction
> Replace Thunder Cloud cloud-demand broadcast
> Language icon replacement
> 
> 3.0.258
> Modify the description text, images and links search search plus split between
> 
> 3.0.257
> Adaptive suspension option list, Google ranked ahead
> 
> 3.0.256
> Toolbars can not use error correction, error correction super drag refresh failure
> 
> 3.0.252
> Super Drag: Drag the page up front to open the link, is down drag link is open in the background, drag the link to the left to open left or right drag link is on the right to open, drag the selected text uses the first a word search program opens.
> 
> 3.0.238
> Jump bar to increase search engine
> 
> 3.0.233
> Language Selection
> 
> 3.0.232
> Increased demand cloud
> 
> 3.0.231
> Settings page, select the menu item prohibit floating
> 
> 3.0.230
> Increase incognito window opens, change the icon to open the background
> 
> 3.0.229
> Increase the default option open in the background, has been selected item and this setting before the check mark opposite, namely: non-default open in the background, the background check will be opened by default open in the background, check the rear is not
> 
> 3.0.227
> Increase in cloud storage
> 
> 3.0.223
> Bug fixes capitalization
> 
> 3.0.221
> Simplify custom search method
> 
> 3.0.216
> Increase express a single query
> 
> 3.0.212
> Open in the background logo displayed on the menu
> 
> 3.0.210
> Fixed BUG Taobao can not search
> Increase Picasa, ask.com, CNN, BBC, etc. 14 Search
> 
> 3.0.206
> New UI, you can set each menu is open in the background or foreground
> 
> 2.1.192
> www.douban.com
> 
> 2.1.191
> Custom Link menu bug fixes
> 
> 2.1.190
> QR decoding abnormal corrected
> 
> 2.1.188
> Send with Gmail. page, link, image, text
> 
> 2.1.185
> Increase open a new tab in the background
> 
> 2.1.184
> Facebook
> 
> 2.1.183
> Increase Thunder Search
> 
> 2.1.181
> Increase on the 1st shop
> 
> 2.1.175
> Chinese Amazon renamed "Amazon China"
> Search for a successful correction chrome24 version of a failed bug
> 
> 2.1.174
> Facebook,Twitter
> 
> 2.1.173
> Increase Sina microblogging Share
> Increase the link menu, QR code, the short URL support links menu
> 
> 2.1.171
> Increase the Google+ button
> 
> 2.1.161
> Reduce access, increased security
> Increase subhead
> Correction Baidu Encyclopedia not search problems
> The correction hotbot can not search for an error
> 
> 2.1.156
> Increase the portfolio of custom search function
> Amendment custom name spaces can not delete errors
> 
> 2.1.151
> Increase word search program menu can not display select content set not displayed by default
> Increase bitsnoop seeds search, courier Search
> 
> 2.1.144
> Increase youtube, ebay, tmall 22 function
> 
> 2.1.143 
> Drag effect optimization
> 
> 2.1.135
> Increase drag and drop sorting, the amendment can not be put in front of custom error
> 
> 2.1.130
> bug fixes, interface tweaks
> 
> 2.1.123
> Amendment to restore the backup did not change the custom error
> increase google.tw, youdao translate a scouring my cool, surfcanyon.com, courier, on the search quickly broadcast, btdigg.org, shopping eDonkey Subscene
> 
> 
> 2.1.114
> Fixed custom search error
> Be amended to delete the search combinatorial search the combination menu does not disappear after error
> Add English Amazon
> 
> 2.1.104
> A brand-new version of a major upgrade options interface, a convenient custom menu, three combinations of search, the size of the QR code custom. No longer limited to a search, will become the chrome essential extension.
> 
> 1.2.56
> Increase goo.gl short URL support, can generate a short URL of the current page, the selected pictures can generate a short URL
> 
> 1.2.53
> Google search can custom domain name, such as: com, com.hk, com.tw
> Increase the hidden right search options menu set
> 
> 1.2.51
> Increase on the shift button, you can choose the order of the search term move up
> Google search using HTTPS
> 
> 1.2.48
> Increase and so on net
> 
> 1.2.45
> Add custom image search function
> Resolve Feedback: use a proxy, google picture search not open or redirect too. I do not know how to modify the image search address
> 
> 1.2.43
> To modify synchronization events triggered
> Taobao switch GBK character set
> 
> 1.2.42
> Increase settings synchronization Tongneng
> 
> 1.2.41
> Added Traditional Chinese support
> To modify BT search eDonkey Search Website
> 
> 1.2.38
> Increase the generated current URL QR code generation capabilities
> 
> 1.2.36
> Add text, images, QR code generation capabilities
> Increase picture QR code recognition
> 
> 1.2.29
> Add custom search function
> Increase backup feature
> 
> 1.1.25
> Chrome Event Page technology, background zero resource consumption
> Task Manager to verify that using the right search memory will be released can be used chrome
> 
> 1.0.21
> Increase the right to enter the option
> Description information for search engines to increase
> Increase Chinese Simplified coding support
> After saving message
> Search engines to 85
> 
> 1.0.17
> Release

### [Awesome Host Manager - Chrome Web Store](https://chrome.google.com/webstore/detail/pikaoeecieigblebdddckmlegonlogha '0.0')
> 介绍: 又一个 host 管理工具
> 
> • 秒切 host 无延迟 😎
> • 基于 chrome 代理 ❤️
> • 兼容 socket 代理 🤔
> • 简洁好用，无多余功能 👏

### [Evernote Web Clipper - Chrome Web Store](https://chrome.google.com/webstore/detail/pioclpoplcdbaefihamjohnefbikjilc '0.0')
> 介绍: Goodbye, bookmarks. Hello, Web Clipper!
> Clip the web pages you want to keep. Save them in Evernote. Easily find them on any device. 
> 
> CLIP IT ALL
> - Great for research—clip any article or web page
> - Clip to a specific notebook and assign tags
> - Use Evernote to find clips on any device
> 
> HIGHLIGHT AND SHARE
> - Highlight key text from any website or article
> - Use text and visual callouts to draw attention
> - Share and email clips or create a URL link
> 
> CUSTOMIZE CLIPS
> - Special formats for LinkedIn, Amazon & YouTube
> - Clip Gmail threads and attachments
> - Clip as entire page, selection, or simplified article 
> 

### https://chrome.google.com/webstore/detail/pkclgpgponpjmpfokoepglboejdobkpl
### https://chrome.google.com/webstore/detail/pkedcjkdefgpdelpbcmbmeomcjbeemfm
### [Insight.io for Github - Chrome Web Store](https://chrome.google.com/webstore/detail/pmhfgjjhhomfplgmbalncpcohgeijonh '0.0')
> 介绍: Improve GitHub code browsing experience by decorating file page with x-ref.
> Insight.io understands the semantics of a lot of Java, Scala, C++/C, Golang, Ruby, Python, PHP repositories at github. 
> 
> Handy features:
> * View the structure of a file(classes, functions)
> * Find the definition of a symbol(across github repos)
> * View all references of a definition(across github repos)
> * Code Intelligence support on Pull Request and Commit Page
> * List the repository in a tree structure
> * View on Insight.io
> 
> Visit https://insight.io for more information.

### [Push to Kindle - Chrome Web Store](https://chrome.google.com/webstore/detail/pnaiinchjaonopoejhknmgjingcnaloc '0.0')
> 介绍: Push to Kindle is a free service which lets you send web articles (news stories, blog posts, Wikipedia entries, etc.) to your Kindle or other e-reader for easy reading. 
> 
> Installing this extension will add a send to Kindle button to your Chrome browser. Simply click the Push to Kindle button on a page which you'd like to read on your Kindle.
> 
> Use Push to Kindle to send a long web article to your Kindle to read it later. Use it to build up a reading list of articles for offline reading. Or simply use it to improve your reading experience.
> 
> Features:
> 
> ★ Speedy delivery to your Kindle
> ★ Preview showing you what will get sent to the Kindle
> ★ Alternative download options: EPUB, MOBI or PDF
> ★ Send to multiple Kindle devices (enter up to 5 comma separated addresses)
> ★ PDF support
> ★ Image support
> ★ Title editing
> ★ Free
> 
> If you're confused about the email addresses needed to use Push to Kindle, please read our guide here: http://help.fivefilters.org/customer/portal/articles/178337-kindle-e-mail-address
> 
> Android users: Look for Push to Kindle in the Android Market https://market.android.com/details?id=org.fivefilters.kindleit
> 
> Kindle Fire users: Look for Push to Kindle in the Amazon App Store http://www.amazon.com/FiveFilters-org-Push-to-Kindle/dp/B005GFM0H0
> 
> iPhone and iPad users: Use our e-mail service http://fivefilters.org/kindle-it/#email
> 
> - - - - - - - - - -
> 
> Push to Kindle can send to the following devices:
> 
> ★ Kindle e-readers sold by Amazon
> 
> ★ Android Kindle app
> 
> ★ iPhone/iPad Kindle app
> 
> - - - - - - - - - -
> 
> Need article suggestions to test Push to Kindle?
> 
> ★ Brainwashing the polite and professional way
> http://johnpilger.com/articles/brainwashing-the-polite-and-professional-way
> 
> ★ Ten Years Of Media Lens
> http://medialens.org/index.php?option=com_content&view=article&id=626:ten-years-of-media-lens-operation-rheinuebung&catid=24:alerts-2011&Itemid=68
> 
> ★ The Propaganda Model: An Overview
> http://www.chomsky.info/onchomsky/2002----.htm
> 
> - - - - - - - - - -
> 
> Push to Kindle: http://fivefilters.org/kindle-it/
> Questions/support: help (at) fivefilters.org
> Twitter: https://twitter.com/fivefilters
> 
> - - - - - - - - - -
> 
> PERMISSIONS AND PRIVACY
> 
> Google Chrome may warn you about permissions required for this extension. This section explains how this extension treats your data.
> 
> Firstly, this extension does not do anything unless you click the Push to Kindle button. We do not monitor or inject any scripts into your pages while you browse.
> 
> When you click the Kindle icon, this extension sends only the URL of the current tab you have open to the Push to Kindle service. The Push to Kindle service then makes its own request for content at that URL and shows you a preview of what it thinks is the content block.
> 
> If the web page you are viewing does not point to publically accessible content, we will not be able to retrieve it. For example, if you invoke Push to Kindle (by mistake, perhaps) while you're reading an email on GMail, or viewing your bank statement, that content will not be accessible to the Push to Kindle service run by FiveFilters.org nor to Amazon.
> 
> Content which is publically accessible and which you process with the Push to Kindle service will be cached on the server for a short period. If you provide email details to enable delivery to your Kindle device, we do not store nor cache the supplied email address on the server once the Kindle document has been sent to Amazon for delivery to your Kindle. The remember checkbox uses local storage on your browser.
> 
> Feel free to contact us if you have any questions.

### [Secure Shell - Chrome Web Store](https://chrome.google.com/webstore/detail/pnhechapfaindjhompbnflcldabbghjo '0.0')
> 介绍: Secure Shell is an xterm-compatible terminal emulator and stand-alone ssh client for Chrome.  It uses Native-Client to connect directly to ssh servers without the need for external proxies.
> 
> If you are using Chrome OS, this is the App version for you.  All other platforms should use the extension version instead.
> 
> It has been well tested for a couple of years.
> 
> Please read the FAQ, available here: https://goo.gl/muppJj.  You can also exchange feedback in the chromium-hterm mailing list, available here: https://goo.gl/RYHiK.
> 
> The changelog is available here: https://goo.gl/YnmXOs

### [Diigo Web Collector - Capture and Annotate - Chrome Web Store](https://chrome.google.com/webstore/detail/pnhplgjpclknigjpccbcnmicgcieojbh '0.0')
> 介绍: Diigo is the #1 extension for annotating, archiving and bookmarking webpages.  
> 
> With this easy-to-use tool, you can 
> 
> 1.  Bookmark links to archive webpages or to read later
> 2.  Attach highlights & stickies to a webpage as a reminder
> 3.  Share pages with annotation via Twitter, Facebook, Google Buzz
> 4.  Access anywhere, via iPhone, iPad (http://bit.ly/e2ujpL), Android  (http://goo.gl/tvbuq). 
> 5.  Create groups to pool findings, share resources or curate content
> 6.  Automatically cross-post to social bookmarking site Delicious (optional)
> 
> 【For Those with Privacy Concern 】
> Chrome will alert you that the extension may access all your data.
> Here is the whole story:
>    This extension has bookmark, highlight and add sticky note features. These features need the privilege to access your pages. However, we never collect any of your data unless you select some content and choose to send it to diigo. Don't worry. We are also internet users and don't want to be evil.
> 
> Recent updates
> * More robust twitter OAuth
> * [new] Search your Diigo library simultaneously while searching google
> * [new option] Load bookmarking info automatically. When enabled, the browser action icon will indicate whether current page is bookmarked.
> * [new] Upload cache page. Save a copy of the web page to My Library.
> * Diigo+Google search in context menu: Select some text, right click and search your library! (can be disabled in options)
> * New option: "Show highlights automatically".  When enabled, annotations on a page will be displayed automatically 
> 
> 【Bug Report and Suggestions】
> We appreciate and receive many user suggestions and requests for improvements. If you have features you would like to see added, or experience a bug for reporting, please send us e-mail at 【developer@diigo.com】. Doing so will allow us to consider any improvements and correct any bugs as soon as possible. Thank you!
> 
> 【More Great Chrome Apps/Extensions by Diigo】 Check them out:
> http://bit.ly/hDJ5se   You won't be disappointed!
> 
> Changelog: http://appchangelog.com/extension/2/Diigo-Web-Collector-Capture-and-Annotate
> 

### [Search Jump Around - Chrome Web Store](https://chrome.google.com/webstore/detail/pnkobkgmlcblgabbombdefkjclhhpjoh '0.0')
> 介绍: Intro | 简介
> 
> This is a modified version of SearchJump by Dave Child, supporting major global and Chinese search engines.
> Special Thanks to Dave Child.
> 
> 这脚本的作用是在搜索页面中的右上角（位置可自定义，见下）加入一个浮动条，提供跳转到其他搜索引擎的链接，方便获取更多搜索结果。浮动条平时半透明且只露半边脸，完全不影响你的浏览体验；需要跳转的时候，只要把鼠标移到该浮动条上，它就会全面展开，为你清晰指路！
> 支持搜索引擎： Google ，百度，360so, 有道，必应，Ask.com ，谷歌
> 
> 代码基于 Dave Child 的 SearchJump 脚本，主要针对中国大陆网友。
> 
> Latest | 最近更新
> 
> 增加设置对话框和设置按钮。
> 可自定义跳转条位置。欢迎测试反馈！
> 
> Customization | 可自定义项
> 
> 通过跳转条下方的“O”——设置按钮打开设置对话框，可自定义跳转链接是否在新窗口打开、跳转条放在左还是右、以及跳转条的垂直位置。
> 
> －－－－－－
> 搜索引擎的相关参数需要更改脚本“## Customization | 自定义区 ##”区的代码，脚本开头有详细注释说明。
> 除非你清楚应该怎么做，否则请发问或请人帮忙。
> 
> 
> Update Log | 更新记录
> 
> 2009.11.07 添加谷歌引擎；修改布局样式，避免被遮住的问题和方便应用自定义样式。
> 2009.11.08 代码完善和修正。
> 2009.11.11 添加专门修正百度URL编码不兼容的功能。
> 2009.12.02 现在浮动条不需要等待载入进度完成即可显示。
> 2009.12.26 将网站图标嵌入代码，现在不需要等待那些网站响应和发出跨站请求了。
> 2010.01.10 增加显示／不显示网站图标的选项（默认显示），需要者请在代码中说明在指定位置更改。
> 2010.01.13 必应的网址修正。
> 2010.01.25 增加在新窗口／当前页面打开跳转网页的选项（默认在新窗口打开）。
> 2010.08.02 Version 2.00beta 新增新的“智能”判断方式，自动提供其他引擎对应的搜索功能跳转，例如在 Google 图片搜索页会自动提供其他引擎的图片搜索跳转。新增新的引擎名称提示方式，不用时界面占用更少空间。欢迎测试反馈！
> 2010.08.05 Version 2.00 更新取得百度关键词的方式；精简一下代码。| Version 2.00a 修正有道地图项上的疏忽。
> 2010.12.23 Version 2.10 加入设置对话框，加入可自定义位置功能。
> 2011.03.24 Version 2.10a 修正有道地图的搜索网址。
> 2011.04.11 Version 2.10b 修正向控制台输出运作数据的遗留。
> 2011.04.21 Version 2.10c 修正在Google图片搜索没提供图片搜索跳转的问题（Google又在URL上玩新花样）。
> 2012.12.25 Version 2.10d 添加Google的https支持，更换设置按钮图标。


Process finished with exit code 0

