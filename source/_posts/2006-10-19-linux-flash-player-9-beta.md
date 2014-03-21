---
title: Linux Flash Player 9 beta !
author: TaopaiC
layout: post
permalink: /2006/10/19/166
tags:
  - 
pt_metakey_img:
  - 's:186:"a:3:{s:3:"img";s:55:"http://static.flickr.com/104/273695795_30941d5c0d_m.jpg";s:3:"alt";s:24:"Screenshot-關於 Plugin";s:3:"url";s:47:"http://www.flickr.com/photos/taopaic/273695795/";}";'
wheredidtheycomefrom:
  - 's:68:"a:5:{i:0;i:127;i:1;i:167;i:2;s:3:"192";i:3;s:3:"147";i:4;s:3:"148";}";'
categories:
  - Linux
  - Software
---
[<img src="http://static.flickr.com/104/273695795_30941d5c0d_m.jpg" alt="Screenshot-關於 Plugin" align="right" height="209" width="240" />][1]剛剛[官方部落格][2]終於放出 beta 版, 還在製作簡易安裝的包裝, 但現在先放出 tarball .

除了可以看 flash 9 以外, **影音不同步**的問題解決了.

討論區沒看到災情, 但是我使用 flash 9 正常, 切換頁面時, [firefox][3] 就會當掉&#8230; <!--more-->

  
安裝很簡單, 先到[這裡][4]下載 Download Installer for Linux (GZ, 2.48 MB) , 並將他解開.

> tar zxvf FP9\_plugin\_beta_101806.tar.gz

再將 libflashplayer.so 複製到 firefox 的 plugins 目錄. ( 以 [Ubuntu Linux][5] 為例 )

> sudo cp flash-player-plugin-9.0.21.55/libflashplayer.so /usr/lib/firefox/plugins

重新開啟 firefox 即可使用了.  
可以利用[這頁][6]看現在使用的 flash player 版本.

如果想回覆之前的版本, 執行 update-flashplugin 即可.

參考連結:

*   [Flash 9 Beta Finally Live &#8211; Ubuntu Forums ][7]
*   [digg &#8211; Flash 9 beta available for Windows, Mac, and Linux][8]

 [1]: http://www.flickr.com/photos/taopaic/273695795/ "Photo Sharing"
 [2]: http://blogs.adobe.com/penguin.swf/2006/10/beta_is_live.html
 [3]: http://www.mozilla.com/firefox/
 [4]: http://labs.adobe.com/downloads/flashplayer9.html
 [5]: http://www.ubuntu.com/
 [6]: http://www.adobe.com/products/flash/about/
 [7]: http://www.ubuntuforums.org/showthread.php?t=279991
 [8]: http://digg.com/linux_unix/Flash_9_beta_available_for_Windows_Mac_and_Linux