---
title: Ubuntu edgy 連到 windows vista 的遠端桌面
author: TaopaiC
layout: post
permalink: /2007/01/07/176
tags:
  - 
wheredidtheycomefrom:
  - 's:75:"a:5:{i:0;s:2:"80";i:1;s:3:"209";i:2;s:3:"127";i:3;s:3:"175";i:4;s:3:"177";}";'
categories:
  - Linux
---
這禮拜把實驗室的電腦換成 windows vista  
回家用 ubuntu 上的遠端桌面連線連不過去&#8230;

只要把 [rdesktop][1] 從 1.4.1 更新到 1.5 即可..  
不過 edgy 上的還是 1.4.1 , 需要自己編新的.

連線速度比 XP 的遠端桌面慢很多 <img src='http://pctao.org/wp-includes/images/smilies/icon_sad.gif' alt=':(' class='wp-smiley' /> 

<!--more-->請參考

  
[ HowTo install rdesktop1.5 (Remote Desktop) including SeamLess Windows and much m  
ore..][2]

ps. 我是把自己編譯的放在 /usr/local/bin 裡. 而不是覆蓋舊版的.  
ps2. 上面那篇還有 SeamlessRDP 的用法, 有興趣的可以看一下.

 [1]: http://www.rdesktop.org/
 [2]: http://ubuntuforums.org/showthread.php?t=224212