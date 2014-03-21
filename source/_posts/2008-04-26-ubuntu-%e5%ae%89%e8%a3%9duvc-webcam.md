---
title: '[ubuntu] 安裝uvc webcam'
author: TaopaiC
layout: post
permalink: /2008/04/26/227
wheredidtheycomefrom:
  - 's:54:"a:5:{i:0;i:174;i:1;i:228;i:2;i:166;i:3;i:147;i:4;i:2;}";'
pt_metakey_img:
  - 's:214:"a:2:{s:3:"img";s:135:"http://partner.monday.com.tw/pub/gd.ashx?s=2&amp;gdid=675261&amp;mcode=MV9jWkhDUnNmbGxVa2NyU2tpMDlGa3ZnZWVKU0psU1VXNEV5d092ZVNEa0IwPQ==";s:3:"alt";s:36:"微軟網路攝影機 VX-7000 (銀) ";}";'
categories:
  - Linux
---
前幾天買了一個新的webcam, 不幸的是 ubuntu 8.04 內附的 [uvcvideo][1] 並不支援, 需要更新的 uvcvideo 才能使用.  
自己編譯其實不麻煩, 用svn下載新的程式碼,make,make install就可以收工了

壞消息是 uvcvideo 只支援新的 Linux 的 Video API: V4L2 (Video For Linux 2), 並不向下支援 V4L1 , 也就是說 [camorama][2] 等軟體都不能使用. 可以安裝 luvcview 測試有沒有安裝成功.

我買的是 [Microsoft LifeCam VX-7000][3] , usb id 是 045e:0723 .<!--more-->

<div>
  <a href="http://partner.monday.com.tw/pub/gotobuy.ashx?gdid=675261&mcode=MV9jWkhDUnNmbGxVa2NyU2tpMDlGa3ZnZWVKU0psU1VXNEV5d092ZVNEa0IwPQ=="><img src="http://partner.monday.com.tw/pub/gd.ashx?s=2&gdid=675261&mcode=MV9jWkhDUnNmbGxVa2NyU2tpMDlGa3ZnZWVKU0psU1VXNEV5d092ZVNEa0IwPQ==" border="0" alt="微軟網路攝影機 VX-7000 (銀) " width="135" height="135" align="right" /></a>(含廣告推薦連結) <a href="http://shopping.pchome.com.tw/ally.html?ally=A00003365&url=http://shopping.pchome.com.tw/?mod=item&func=exhibit&IT_NO=DCAD37-A16925144 ">PCHOME</a>或是<a href="http://partner.monday.com.tw/pub/gotobuy.ashx?gdid=675261&mcode=MV9jWkhDUnNmbGxVa2NyU2tpMDlGa3ZnZWVKU0psU1VXNEV5d092ZVNEa0IwPQ==">興奇購物</a>都有賣, 評價請看<a href="http://www.everythingusb.com/microsoft-lifecam-vx-7000-14105.html">國外這篇評論</a>, 我是買了才看到評論 <img src='http://pctao.org/wp-includes/images/smilies/icon_sad.gif' alt=':(' class='wp-smiley' /> 價錢跟L社便宜不少, 但是效果&#8230; 也還好啦 /_\</p> <h3>
    uvcvideo 安裝過程
  </h3>
  
  <h4>
    下載程式碼
  </h4>
  
  <p>
    如果沒有安裝svn的話, 請先<br /> <code>sudo apt-get install subversion</code><br /> 用 svn 下載新版程式碼<br /> <code>svn checkout svn://svn.berlios.de/linux-uvc/linux-uvc/trunk</code>
  </p>
  
  <h4>
    安裝kernel header
  </h4>
  
  <p>
    <code>sudo apt-get install linux-headers-`uname -r`</code>
  </p>
  
  <h4>
    改makefile
  </h4>
  
  <p>
    因為ubuntu放uvcvideo.so的位置和預設的不太一樣,需要修改一下安裝位置<br /> <code>INSTALL_MOD_DIR := usb/media&lt;br />
to&lt;br />
INSTALL_MOD_DIR := ubuntu/media/usbvideo&lt;br />
</code>
  </p>
  
  <h4>
    安裝
  </h4>
  
  <p>
    <code>make install</code>
  </p>
  
  <h4>
    重載 uvcvideo
  </h4>
  
  <p>
    <code>sudo modprobe -r uvcvideo&lt;br />
sudo modprobe uvcvideo</code><br /> 應就可在dmesg看到
  </p>
  
  <blockquote>
    <p>
      [46167.743036] uvcvideo: Found UVC 1.00 device Microsoft� LifeCam VX-7000 (045e:0723)<br /> [46167.744808] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -32 (exp. 26).<br /> [46167.754655] input: Microsoft� LifeCam VX-7000 as /devices/pci0000:00/0000:00:1d.7/usb5/5-2/5-2:1.0/input/input15<br /> [46167.779862] usbcore: registered new interface driver uvcvideo<br /> [46167.779873] USB Video Class driver (SVN r205)
    </p>
  </blockquote>
  
  <p>
    每次更新 kernel 時都要重新編譯安裝.. 直到內建的 uvcvideo 支援為止.
  </p>
  
  <h3>
    luvcview &#8211; uvc webcam 的觀看程式
  </h3>
  
  <p>
    <code>sudo apt-get install luvcview</code>
  </p>
  
  <h4>
    簡易使用
  </h4>
  
  <p>
    <code>luvcview -d device&lt;br />
例如&lt;br />
luvcview -d /dev/video0</code>
  </p>
  
  <h4>
    常用參數
  </h4>
  
  <p>
    <code>-L 列出支援的格式&lt;br />
-l  列出支援的控制或設定&lt;br />
-s 影像大小 (寬x高)&lt;br />
-f 影像格式 (jpg, yuv)</code><br /> 其他就請看 luvcview -h
  </p>
  
  <h3>
    參考連結
  </h3>
  
  <ul>
    <li>
      <a href="http://linux-uvc.berlios.de/">Linux UVC driver & tools</a> &#8211; uvcvideo 首頁, 有支援硬體列表
    </li>
    <li>
      <a href="https://help.ubuntu.com/community/UVC">UVC &#8211; Community Ubuntu Documentation</a>
    </li>
  </ul>
</div>

 [1]: http://linux-uvc.berlios.de/
 [2]: http://camorama.fixedgear.org/
 [3]: http://www.microsoft.com/taiwan/hardware/digitalcommunication/productdetails.aspx?pid=011