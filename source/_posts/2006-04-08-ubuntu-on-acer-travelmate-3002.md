---
title: ubuntu on Acer TravelMate 3002
author: TaopaiC
layout: post
permalink: /2006/04/08/129
tags:
  - 
wheredidtheycomefrom:
  - 's:44:"a:3:{i:0;i:130;i:1;s:3:"127";i:2;s:3:"227";}";'
categories:
  - Linux
---
ubuntu 裝在 Acer TM3002 上面有不小的問題, 不能說是 ubuntu 的問題, 應該是 acer 的 bios 和 linux kernel 之間的問題 <img src='http://pctao.org/wp-includes/images/smilies/icon_sad.gif' alt=':(' class='wp-smiley' /> 

要在 kernel 的選項加入 noacpi , 不然無法開機, 但是 noacpi 又會導致音效卡等其他裝置失效 (我不確定還有那些裝置失效) , 有許多地方要修正才能使用&#8230; 之前裝 Gentoo 時, 有按照找到的資料修正了部份, 但還不算很完美.  
<!--more-->

  
所以我的筆電半年前加裝 Gentoo 後, 就閒置在那. 最近把 Gentoo 換成 ubuntu , 也因為一樣的問題, 所以不常使用.  
前天看到 ubuntu 討論區, 有人貼了一篇說他使用 2.6.16 的 kernel , 很愉快.  
看了一下 2.6.16 的 [ChangeLog][1] , 他修正了[Bug4700][2] , 這個以前要自行 patch 的東西直接放進 kernel 了 <img src='http://pctao.org/wp-includes/images/smilies/icon_biggrin.gif' alt=':D' class='wp-smiley' /> 

> [PATCH] i386: Handle non existing APICs without panicing
> 
> [description from AK]
> 
> This fixes booting in APIC mode on some ACER laptops. x86-64  
> did a similar change some time ago.
> 
> See http://bugzilla.kernel.org/show_bug.cgi?id=4700 for details 

所以 kernel 是 2.6.16 以後的 LiveCD , 就不需要作特殊修正, 就可以使用在 acer 筆電上了!!

我現在在筆電安裝自行編譯的 2.6.16.1 kernel , 以及之前裝的 DSDT.aml (不太確定這個現在有沒有影響), cvs版的alsa , 筆定的功能差不多都能使用. 音效, 螢幕, 電池, CPU Frequency scaling , 藍牙都看起來可以用, 但不能休眠.

註1: 前幾天因為這個問題, 還想把這台筆電賣掉 /.\  
註2: BUG4700討論串裡, 有 acer 官網找不到的官方檔案下載網站, 以及一個來賓帳號/密碼. 裡面有比台灣網站更新的 bios, 3B09 和 3B14 &#8230;

<ins datetime="2006-04-24T03:37:36+00:00"><br /> UPDATE: ubuntu 的 2.6.15-21 kernel 已經將這個 patch 納入, 可以不加 noacpi 參數正常開機了. (詳見 <a href="https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/35795">Bug #35795</a> 或 <a href="http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-source-2.6.15/linux-source-2.6.15_2.6.15-20.30/changelog">Changelog</a> )</p> 
  <p>
    看來, 下一版的就可以正常安裝使用, 不需要特殊調整了!<br /> </ins>
  </p>

 [1]: http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.16
 [2]: http://bugzilla.kernel.org/show_bug.cgi?id=4700