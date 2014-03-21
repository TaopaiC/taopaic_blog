---
title: 解決 flash 文字無法顯示的問題 (on Ubuntu edgy)
author: TaopaiC
layout: post
permalink: /2006/10/03/148
tags:
  - ubuntu edgy flash
wheredidtheycomefrom:
  - 's:56:"a:5:{i:0;i:256;i:1;i:192;i:2;i:127;i:3;i:166;i:4;i:149;}";'
pt_metakey_img:
  - 's:179:"a:3:{s:3:"img";s:55:"http://static.flickr.com/111/258880286_7b76176b1b_t.jpg";s:3:"alt";s:17:"flashWithoutWords";s:3:"url";s:47:"http://www.flickr.com/photos/taopaic/258880286/";}";'
categories:
  - Linux
---
[<img src="http://static.flickr.com/111/258880286_7b76176b1b_t.jpg" title="flashWithoutWords" alt="flashWithoutWords" align="right" height="100" width="95" />][1]最近發現用firefox看有flash的網頁總是怪怪的, 剛剛連去<a href="http://www.chinatrust.com.tw/" target="_blank">中國信託</a>的網頁, 才發現flash裡面的文字無法顯示, 所以網頁看起來怪怪的&#8230; 選單看不到文字, 根本無法使用網路銀行&#8230; /_\  
找了許多網頁, 都不外乎說要安裝 msttcorefonts 和 gsfonts-x11 , 前者是我必裝的字型套件, 後者是 flashplayer-nonfree 的依賴套件, 所以這兩個套件我都有安裝, 這個解法對我無效. 奇怪的是, 我的notebook使用同一版本的<a href="http://www.ubuntu.com/" target="_blank">ubuntu linux</a>, 差不多一樣的環境, 卻沒這個問題.

最後在 <a href="http://www.flickr.com/forums/bugs/2589" target="_blank">FlickrBugs</a> 那邊找到解法, 提到另一種方法,

> % cd /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType/  
> % sudo ttmkfdir ./  
> % sudo mkfontdir ./

( 如果沒有 ttmkfdir 這個指令的話, 請安裝 ttmkfdir 套件 )  
[<img src="http://static.flickr.com/112/258881375_00d58e6e05_t.jpg" title="flashWithWords" alt="flashWithWords" align="left" height="80" width="100" />][2]

我就檢查桌機和notebook的該目錄, 確實就是桌機缺少 fonts.dir 這個檔案. 執行 mkfontdir 之後, flash 就可以顯示文字了~

參考資料:

*   <a href="http://www.flickr.com/forums/bugs/2589" target="_blank">Flickr: Forums: FlickrBugs: Firefox, Linux, Flash problem</a>
*   <a href="http://linux.inet.hr/flash_plugin_on_x11r7.html" target="_blank">The flash plugin and X.Org 7.0 (X11R7) font problems</a>

 [1]: http://www.flickr.com/photos/taopaic/258880286/ "Photo Sharing"
 [2]: http://www.flickr.com/photos/taopaic/258881375/ "Photo Sharing"