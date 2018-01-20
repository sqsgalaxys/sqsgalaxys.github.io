---

title: Python 爬虫爬取 chrome webstore  
date: 2018-01-14 23:34:58  
tags:  

---



# Python 爬虫爬取 chrome webstore

插件本地存放目录:  
`~/Library/Application Support/Google/Chrome/Default/Extensions`

`插件地址 = 'https://chrome.google.com/webstore/detail/' + 插件存放目录里的文件夹名`

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
            soup = BeautifulSoup(html_source, 'html.parser')
            # <h1 class="e-f-w">OneTab</h1>
            # 插件的标题
            # print("标题: " + soup.html.find_all("title")[0].text)
            # 合成 markdown 链接
            title = soup.html.find_all("title")[0].text
            print('### [' + title + ']' + '(' + url + " '0.0'" + ')')
            # <pre class="C-b-p-j-Oa">
            # 插件的自我介绍
            print(soup.find_all("pre", class_="C-b-p-j-Oa")[0].text)
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



参考:
- [你的Chrome插件都装到哪了？](http://lazybios.com/2016/11/chrome-plugin-location-in-your-system/ '0.0')  
