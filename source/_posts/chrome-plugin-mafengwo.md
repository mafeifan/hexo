---
title: 开发了一款chrome扩展
date: 2018-02-08 11:49:33
tags: chrome
---

[1]:/images/180208_chrome-plugin-mafengwo/1.png
[2]:/images/180208_chrome-plugin-mafengwo/2.gif

<!--more-->

闲暇时候喜欢去[马蜂窝](http://www.mafengwo.cn/)这个网站看一些用户写的游记，其中有些配的背景音乐蛮好听的。比如[这个](http://www.mafengwo.cn/i/8332498.html)，如果想下载下来，对一个程序员来说是件非常容易的事情。
只需右键 - 审查元素，找到并复制audio音乐标签的真实地址，最后用下载软件下载就可以了。

![param][1]

对于普通用户就不那么方便了。而且出于对自己的需求，我就开发了一款基于chrome浏览器的扩展程序。
有如下功能：
1. 打开有背景音乐的游记页面，自动弹出通知。显示该歌曲的歌手，专辑和风格等信息。
2. 右键菜单可下载该歌曲。

![param][2]

### 相关链接：
[webstore下载地址](https://chrome.google.com/webstore/detail/mafengwo-mp3-downloader/olngcgpfadeplnlikpbklbgbkahhgccp)
[源码托管在github](https://github.com/mafeifan/mafengwo-mp3-downloader)

关于如何将chrome插件发布到webstore上面，这里有[官方教程](https://developer.chrome.com/webstore/publish)，还需要支付5美元，可以用信用卡，我建议办一张招商的全币种信用卡，很方便。
支付时国家地区选择香港。然后找个香港的地址填下就行了。
