---
title: Use Chrome
date: 2016-08-08 17:02:17
update:
tags: [Use,Chrome]
---


<!-- more -->
- [copy 2 clipboard with ease - Chrome 网上应用店](https://chrome.google.com/webstore/detail/copy-2-clipboard-with-eas/hiiobhaaokpmdmkkcaokdlanlemmcoah "")
`[title](url "")`
- [LastPass: Free Password Manager - Chrome 网上应用店](https://chrome.google.com/webstore/detail/lastpass-free-password-ma/hdokiejnpimakedhajhdlcegeplioahd "")
- [Vim Tips - New Tab Replacement - Chrome 网上应用店](https://chrome.google.com/webstore/detail/vim-tips-new-tab-replacem/lbhnkgjaoonakhladmcjkemebepeohkn "")
- [OneTab - Chrome 网上应用店](https://chrome.google.com/webstore/detail/onetab/chphlpgkkbolifaimnlloiipkdnihall "")
- [Vimium - Chrome 网上应用店](https://chrome.google.com/webstore/detail/vimium/dbepggeogbaibhgnhhndojpepiihcmeb "")
## Vimium

### Navigating the current page:

    ?       show the help dialog for a list of all available keys
    // 左右滑动
    h       scroll left 
    l       scroll right
    j       scroll down
    k       scroll up
    gg      scroll to top of the page
    G       scroll to bottom of the page
    // 向上下滑动半页
    d       scroll down half a page
    u       scroll up half a page
    f       open a link in the current tab
    F       open a link in a new tab
    // 重新加载页面
    r       reload
    // 查看网页源码
    gs      view source
    // 进入插入模式
    i       enter insert mode -- all commands will be ignored until you hit Esc to exit
    // 拷贝当前标签的链接
    yy      copy the current url to the clipboard
    // 选择一个链接拷贝
    yf      copy a link url to the clipboard
    // frame 
    gf      cycle forward to the next frame
    gF      focus the main/top frame

### Navigating to new pages:

    // 打开链接,书签,历史
    o       Open URL, bookmark, or history entry
    O       Open URL, bookmark, history entry in a new tab
    // 打开书签
    b       Open bookmark
    B       Open bookmark in a new tab

### Using find:

    /       enter find mode
              -- type your search query and hit enter to search, or Esc to cancel
    n       cycle forward to the next find match
    N       cycle backward to the previous find match

For advanced usage, see [regular expressions](https://github.com/philc/vimium/wiki/Find-Mode) on the wiki.

### Navigating your history:

    H       go back in history
    L       go forward in history

### Manipulating tabs:

    J, gT   go one tab left
    K, gt   go one tab right
    g0      go to the first tab
    g$      go to the last tab
    ^       visit the previously-visited tab
    t       create tab
    yt      duplicate current tab
    x       close current tab
    X       restore closed tab (i.e. unwind the 'x' command)
    T       search through your open tabs
    <a-p>   pin/unpin current tab

### Using marks:

    ma, mA  set local mark "a" (global mark "A")
    `a, `A  jump to local mark "a" (global mark "A")
    ``      jump back to the position before the previous jump
              -- that is, before the previous gg, G, n, N, / or `a

### Additional advanced browsing commands:

    ]], [[  Follow the link labeled 'next' or '>' ('previous' or '<')
              - helpful for browsing paginated sites
    <a-f>   open multiple links in a new tab
    gi      focus the first (or n-th) text input box on the page
    gu      go up one level in the URL hierarchy
    gU      go up to root of the URL hierarchy
    ge      edit the current URL
    gE      edit the current URL and open in a new tab
    zH      scroll all the way left
    zL      scroll all the way right
    v       enter visual mode; use p/P to paste-and-go, use y to yank
    V       enter visual line mode

Vimium supports command repetition so, for example, hitting `5t` will open 5 tabs in rapid succession. `<Esc>` (or
`<c-[>`) will clear any partial commands in the queue and will also exit insert and find modes.

There are some advanced commands which aren't documented here; refer to the help dialog (type `?`) for a full
list.

Custom Key Mappings


## 参考:
- [philc/vimium: The hacker's browser.](https://github.com/philc/vimium#keyboard-bindings "")
- [Home · philc/vimium Wiki](https://github.com/philc/vimium/wiki "")
