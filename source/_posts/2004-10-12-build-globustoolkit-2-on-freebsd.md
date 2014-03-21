---
title: build GlobusToolkit 2 on FreeBSD
author: TaopaiC
layout: post
permalink: /2004/10/12/9
wheredidtheycomefrom:
  - 's:40:"a:3:{i:0;i:10;i:1;s:1:"6";i:2;s:2:"97";}";'
categories:
  - AccessGrid
  - FreeBSD
---
為了要裝 gt2 , 新弄一個 FreeBSD 5 的環境, 從 misc/globus2 安裝.  
紀錄一下.

之前在另外一台 FreeBSD 5 上安裝, 就不順利, 這次順利的很, 不知道是哪裡問題 <img src='http://pctao.org/wp-includes/images/smilies/icon_neutral.gif' alt=':|' class='wp-smiley' /> 

<!--more-->

> FreeBSD EVA10 5.2.1-RELEASE FreeBSD 5.2.1-RELEASE #0: Mon Feb 23 20:45:55 GMT 2004 root@wv1u.btc.adaptec.com:/usr/obj/usr/src/sys/GENERIC i386 

> cvsup-without-gui-16.1h = up-to-date with port  
> expat-1.95.8 = up-to-date with port  
> ezm3-1.1 < needs updating (port has 1.2)  
> gettext-0.13.1_1 = up-to-date with port  
> globus-2.4.3_1 = up-to-date with port  
> gmake-3.80_2 = up-to-date with port  
> gpt-3.1_1 = up-to-date with port  
> libiconv-1.9.2_1 = up-to-date with port  
> libtool-1.3.5_2 = up-to-date with port  
> libtool-1.5.8 = up-to-date with port  
> makepatch-2.00a_1 = up-to-date with port  
> p5-Archive-Tar-1.10 = up-to-date with port  
> p5-Compress-Zlib-1.33 = up-to-date with port  
> p5-Digest-1.08 = up-to-date with port  
> p5-Digest-MD5-2.33 = up-to-date with port  
> p5-File-Spec-0.86 = up-to-date with port  
> p5-IO-Zlib-1.01 = up-to-date with port  
> p5-MIME-Base64-3.03 = up-to-date with port  
> p5-PodParser-1.28_1 = up-to-date with port  
> p5-Test-Harness-2.42 = up-to-date with port  
> p5-Test-Simple-0.47_1 = up-to-date with port  
> perl-5.6.1_15 = up-to-date with port  
> perl-5.8.5 = up-to-date with port  
> screen-4.0.2_1 = up-to-date with port  
> sudo-1.6.8.1 = up-to-date with port  
> vim-lite-6.3.16 = up-to-date with port