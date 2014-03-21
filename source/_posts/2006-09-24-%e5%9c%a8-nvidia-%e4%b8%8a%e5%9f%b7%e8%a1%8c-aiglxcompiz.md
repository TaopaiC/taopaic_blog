---
title: 在 nVIDIA 上執行 AIGLX/compiz !!!
author: TaopaiC
layout: post
permalink: /2006/09/24/147
tags:
  - compiz beryl linux nvidia
wheredidtheycomefrom:
  - 's:72:"a:5:{i:0;i:163;i:1;s:3:"180";i:2;s:3:"198";i:3;s:3:"207";i:4;s:3:"148";}";'
pt_metakey_img:
  - 's:176:"a:3:{s:3:"img";s:55:"http://static.flickr.com/110/251369627_057301f955_m.jpg";s:3:"alt";s:14:"Screenshot.png";s:3:"url";s:47:"http://www.flickr.com/photos/taopaic/251369627/";}";'
categories:
  - Linux
---
[<img src="http://static.flickr.com/110/251369627_057301f955_m.jpg" alt="Screenshot.png" align="left" height="98" width="240" />][1]前幾天, nVIDIA 釋出 beta 版的 linux driver (新聞: [nZ][2][one][2]), 支援 GLX\_EXT\_texture\_from\_pixmap , 也就是說, AIGLX 也可以在nVIDIA 的顯示卡上使用了!

<p align="left">
  &nbsp;
</p>

<p align="left">
  前幾天自行安裝 driver 一直失敗 <img src='http://pctao.org/wp-includes/images/smilies/icon_sad.gif' alt=':(' class='wp-smiley' /> 今天看到 <a href="http://www.compiz.net/">www.compiz.net</a> 的 repo 裡有提供 beta 版 driver 的套件, 順便和 beryl (以前稱為 <strike>compiz</strike> <ins datetime="2006-10-15T12:46:58+00:00">compiz-quinn , 由 quinn 維護的分支</ins> ) 一起裝起來, 就可以用 beryl 了!!
</p>

<p align="left">
  &nbsp;
</p>

<p align="left">
  抓圖:
</p>

[<img src="http://static.flickr.com/81/251370512_1ba2456e5f.jpg" alt="nvidiaAIGLX.png" height="200" width="500" />][3]

<ins datetime="2006-10-15T12:46:58+00:00">UPDATE: 有興趣的人, 可以參考 <a href="http://www.ubuntuforums.org/showthread.php?t=263851&highlight=blank">HOWTO: Beryl with latest nvidia drivers and Edgy&#8217;s built in AIGLX (no XGL) &#8211; Ubuntu Forums</a> , 我個人是使用 Option 1 的方法, 使用 Aramanth 維護的 nvidia driver包&#8230;</ins>

 [1]: http://www.flickr.com/photos/taopaic/251369627/ "Photo Sharing"
 [2]: http://www.nzone.com/object/nzone_downloads_linux_display_x86_1.0-9625.html
 [3]: http://www.flickr.com/photos/taopaic/251370512/ "Photo Sharing"