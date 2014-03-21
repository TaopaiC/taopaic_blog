---
title: 關掉無用的 apt-get 的 Translation list
author: TaopaiC
layout: post
permalink: /2007/07/27/190
wheredidtheycomefrom:
  - 's:76:"a:5:{i:0;s:3:"127";i:1;s:3:"148";i:2;s:3:"180";i:3;s:3:"191";i:4;s:3:"176";}";'
  - 's:76:"a:5:{i:0;s:3:"127";i:1;s:3:"148";i:2;s:3:"180";i:3;s:3:"191";i:4;s:3:"176";}";'
  - 's:76:"a:5:{i:0;s:3:"127";i:1;s:3:"148";i:2;s:3:"180";i:3;s:3:"191";i:4;s:3:"176";}";'
categories:
  - Linux
---
<ins datetime="2008-09-01T08:44:31+00:00">UPDATE: 現在已有 Translation 的訊息, 不需關閉了.</ins>

每次用 apt-get 更新時, 都會有一堆找不到 Translation 的訊息吧. 我覺得這個挺礙眼的, 就先關掉他吧&#8230;  
<!--more-->

  
這個訊息是這樣的, apt-get update 時, 會去找每個 source 的 Translation-"environment" ,  
我的環境是 zh_TW, 訊息就如下

> pctao@pctao-desktop:/etc/apt$ sudo apt-get update  
> 下載:1 http://archive.ubuntu.com gutsy Release.gpg [191B]  
> 略過 http://archive.ubuntu.com gutsy/main Translation-zh_TW  
> 略過 http://archive.ubuntu.com gutsy/restricted Translation-zh_TW  
> 略過 http://archive.ubuntu.com gutsy/universe Translation-zh_TW  
> 略過 http://archive.ubuntu.com gutsy/multiverse Translation-zh_TW  
> 下載:2 http://archive.ubuntu.com gutsy-updates Release.gpg [191B]  
> 略過 http://archive.ubuntu.com gutsy-updates/main Translation-zh_TW  
> 略過 http://archive.ubuntu.com gutsy-updates/restricted Translation-zh_TW  
> 略過 http://archive.ubuntu.com gutsy-updates/universe Translation-zh_TW  
> 略過 http://archive.ubuntu.com gutsy-updates/multiverse Translation-zh_TW

現在都還沒看到有 Translation-zh_TW , 打開只是看到一堆"略過"訊息, 看了礙眼, 乾脆關掉吧. 以後有這功能再打開使用.

改用這個指令更新, 就不會看到 &#8220;略過 http://&#8230; Translation-zh_TW" 的訊息 (這邊有個BUG,請容我之後說明)

> sudo apt-get update -o APT::Acquire::Translation=none

如果你是 Synaptic 的愛好者, 請執行

> gksu &#8220;synaptic -o APT::Acquire::Translation=none"

或者在 Synaptic 的 &#8220;設定" -> &#8220;設定內部選項" , 變數填入 &#8220;APT::Acquire::Translation" , 值填入 &#8220;none" . 但在下次使用 Synaptic , 還要在做一次.

各位有沒有發現為何不是寫在設定檔, 而是使用參數的方式?  
寫在設定檔的方法:  
在 /etc/apt/apt.conf (如果沒有請自建一個) 中寫入

> APT::Acquire::Translation &#8220;none";

或者在 /etc/apt/apt.conf.d/ 建立一個檔案, 如 /etc/apt/apt.conf.d/80noTranslation , 內容一樣填入

> APT::Acquire::Translation &#8220;none";

應該會成功才對.

但是, 我怎麼測試都不行, 看了一下 apt 的原始碼 (版本 0.7.4ubuntu1), 他讀完設定檔之後, 再用 Translation-"environment" 複寫, 除非用 -c 或是 -o 再去覆蓋, 不然結果都一樣. (apt-pkg/init.cc 110行)