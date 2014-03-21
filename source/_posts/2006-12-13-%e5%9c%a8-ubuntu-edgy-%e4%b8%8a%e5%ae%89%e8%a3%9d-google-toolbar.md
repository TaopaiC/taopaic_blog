---
title: 在 ubuntu edgy 上安裝 Google Toolbar
author: TaopaiC
layout: post
permalink: /2006/12/13/174
tags:
  - 
wheredidtheycomefrom:
  - 's:76:"a:5:{i:0;s:3:"130";i:1;s:3:"166";i:2;s:3:"244";i:3;s:3:"192";i:4;s:3:"175";}";'
categories:
  - Linux
  - Software
---
最近硬碟壞掉, 重灌 ubuntu 才遇到的問題. 裝 [Google Toolbar][1] 時, 會跳出不支援該平台的對話框.

這是 ubuntu / debian 的變種 firefox 的問題. 可以修改 install.rdf 的內容暫時解決.<!--more-->

1.  下載該 .xpi  
    > cd /tmp
    
    > wget http://dl.google.com/firefox/google-toolbar-linux.xpi

2.  解開  
    > mkdir /tmp/google ; cd /tmp/google
    
    > unzip /tmp/google-toolbar-linux.xpi

3.  修改 install.rdf , 將  
    > <em:targetplatform>Linux</em:targetplatform>
    
    改為
    
    > <em:targetplatform>linux-gnu\_x86-gcc3</em:targetplatform>linux-gnu\_x86-gcc3

4.  將檔案封裝回 .xpi  
    > zip -r google-toolbar.xpi *

5.  將做好的 google-toolbar.xpi 拖拉到 firefox 的視窗, 就可以正常安裝了

參考資料:

*   [Google Groups:Google Toolbar Firefox Help][2]
*   [Launchpad: [Edgy] Incompatible with Google Toolbar][3]

 [1]: http://www.google.com/tools/firefox/toolbar/index.html
 [2]: http://groups.google.com/group/FFToolbar-Group-Bugs/browse_thread/thread/3d48b5cf7413904f/5e3db65b97f6e878
 [3]: https://launchpad.net/distros/ubuntu/+source/firefox/+bug/68663