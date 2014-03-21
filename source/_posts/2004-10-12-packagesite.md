---
title: PACKAGESITE
author: TaopaiC
layout: post
permalink: /2004/10/12/12
wheredidtheycomefrom:
  - 's:41:"a:3:{i:0;i:16;i:1;s:2:"11";i:2;s:2:"19";}";'
categories:
  - FreeBSD
---
安裝 package 的懶人方法  
(但還是不保險?)  
記下來在說

<!--more-->

> setenv PACKAGESITE http://example.net/exampledir/ 

然後

> <del>pkg_add -rRv blahblah</del>  
> <ins title="we should record the installation of a package" datetime="2004-9-12T20:56:36--8:00" cite="http://gslin.org/?p=62">pkg_add -rv blahblah</ins> 

Note:

> http://pointyhat.freebsd.org/errorlogs/i386-packages-5-latest/All/