---
title: 'Firefox Widgets &#8211; 改善 ubuntu 的 firefox 外觀'
author: TaopaiC
layout: post
permalink: /2007/10/31/192
wheredidtheycomefrom:
  - 's:68:"a:5:{i:0;i:166;i:1;i:198;i:2;s:3:"195";i:3;s:3:"174";i:4;s:3:"175";}";'
pt_metakey_img:
  - 's:169:"a:3:{s:3:"img";s:57:"http://static.flickr.com/2369/1808469400_fbc19fa751_m.jpg";s:3:"alt";s:0:"";s:3:"url";s:53:"http://www.flickr.com/photos/69004123@N00/1808469400/";}";'
categories:
  - Linux
  - Software
---
Linux 版本的 firefox , 網頁元件很樸實, 跟 windows 版本比起來, 根本就是醜 T_T

改善前 (如果你看慣 windows 版本的 firefox , 就知道 linux 版本的按鈕有多醜)  
[<img src="http://static.flickr.com/2369/1808469400_fbc19fa751_m.jpg" border="0" />][1]  
改善後  
[<img src="http://static.flickr.com/2241/1808469310_c73aaf338d_m.jpg" border="0" />][2]  
Text Field , Radio Button , Button 元件都變得好看許多.  
<!--more-->

首先到 [Firefox Widgets (Ubuntu Forum)][3] 下載檔案.  
下載之後,

> tar jxvf firefox\_widgets\_2.7.tar.bz2  
> cd firefox\_widgets\_2.7  
> ./install  
> 或  
> sudo ./graphic_installer

* 提醒: install 這個 script 裡面有用到 sudo &#8230;. !@#$

選好安裝路徑之後, 安裝, 重啟 firefox 即可看到漂亮的網頁元件了.

如果要避免之後升級時, 檔案會被蓋掉, 可以用

> sudo dpkg-divert &#8211;add <INSERT FIREFOX ROOT DIRECTORY HERE>/res/forms.css

取消

> sudo dpkg-divert &#8211;remove <INSERT FIREFOX ROOT DIRECTORY HERE>/res/forms.css

 [1]: http://www.flickr.com/photos/69004123@N00/1808469400/ "Original Firefox viewing Google Home Page"
 [2]: http://www.flickr.com/photos/69004123@N00/1808469310/ "Firefox with Firefox Widgets viewing Google Home Page"
 [3]: http://ubuntuforums.org/showthread.php?t=369596