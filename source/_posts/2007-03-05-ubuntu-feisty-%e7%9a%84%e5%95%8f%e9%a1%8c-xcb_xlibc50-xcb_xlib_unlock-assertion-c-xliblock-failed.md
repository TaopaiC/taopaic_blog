---
title: 'Ubuntu feisty 的問題: xcb_xlib.c:50: xcb_xlib_unlock: Assertion `c->xlib.lock&#8217; failed.'
author: TaopaiC
layout: post
permalink: /2007/03/05/177
tags:
  - 
wheredidtheycomefrom:
  - 's:44:"a:3:{i:0;i:178;i:1;s:3:"176";i:2;s:3:"179";}";'
categories:
  - Java
  - Linux
---
自從2月初的 libxcb-xlib0 的更新之後, 一些視窗程式都會發生 assertion , 像是 java , vmware 都有影響.

> java: xcb\_xlib.c:50: xcb\_xlib_unlock: Assertion \`c->xlib.lock&#8217; failed.

[X protocol C-language Binding][1] (xcb) 將取代 xlib , 且提供 transport layer 讓尚未修改的程式使用 ( [Xlib/XCB][2] ). 如果原本使用 xlib 的程式沒有照規矩來, 就會發生 assertion. JRE , vmware 這些程式又不是說改就改, 我原本打算等官方做修正, 等了一個月還是沒有, 只好自己動手了.<!--more-->網路上的暫時解法不外兩種, 一個是退回 xlib , 另外一個就是自己編譯, 把 assert 檢查拿掉.

我用後者的方法

> apt-get source libxcb-xlib0  
> sudo apt-get build-dep libxcb-xlib0  
> cd libxcb-1.0  
> edit src/xcb_xlib.c  
> dpkg-buildpackage -rfakeroot -b -uc  
> sudo dpkg -i ../libxcb-xlib0\_1.0-1.1\_i386.deb

重點是 src/xcb_xlib.c 的第 41 , 50 行的 assert 都註解掉. 我參考 [archlinux 的 patch][3] , 把 assert 換成 if . 如下:

> void xcb\_xlib\_lock(xcb\_connection\_t *c)  
> {  
> \_xcb\_lock_io(c);  
> // assert(!c->xlib.lock);  
> if (!c->xlib.lock) {  
> c->xlib.lock = 1;  
> c->xlib.thread = pthread_self();  
> }  
> \_xcb\_unlock_io(c);  
> }
> 
> void xcb\_xlib\_unlock(xcb\_connection\_t *c)  
> {  
> \_xcb\_lock_io(c);  
> // assert(c->xlib.lock);  
> if (c->xlib.lock) {  
> assert(pthread\_equal(c->xlib.thread, pthread\_self()));  
> c->xlib.lock = 0;  
> pthread\_cond\_broadcast(&c->xlib.cond);  
> }  
> \_xcb\_unlock_io(c);  
> }

安裝之後, java, vmware 都能執行, 雖然不知有啥缺點, 但是 java 能跑最要緊!

參考: [ubuntu forums][4]

UPDATE: ubuntu feisty 已預設關掉xcb檢查. 請參閱<a href="http://pctao.org/2007/03/10/179/" title=""[fixed] ubuntu feisty & libxcb 的問題" 的永久鏈接">[fixed] ubuntu feisty & libxcb 的問題</a>

 [1]: http://xcb.freedesktop.org/wiki/ "XCB"
 [2]: http://xcb.freedesktop.org/wiki/XlibXcb "Xlib/XCB"
 [3]: http://cvs.archlinux.org/cgi-bin/viewcvs.cgi/x11-libs/libxcb/xcb_xlib-no-assert-on-lock.patch?rev=1.1&content-type=text/vnd.viewcvs-markup
 [4]: http://ubuntuforums.org/showthread.php?t=368462&page=2