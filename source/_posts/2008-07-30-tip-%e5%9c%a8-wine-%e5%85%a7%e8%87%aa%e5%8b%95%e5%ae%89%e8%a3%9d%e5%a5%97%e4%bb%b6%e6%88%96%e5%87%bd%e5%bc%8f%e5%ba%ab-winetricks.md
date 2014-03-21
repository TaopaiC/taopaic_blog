---
title: '[tip] 在 wine 內自動安裝套件或函式庫 &#8211; winetricks'
author: TaopaiC
layout: post
permalink: /2008/07/30/256
wheredidtheycomefrom:
  - 's:56:"a:5:{i:0;i:227;i:1;i:222;i:2;i:209;i:3;i:127;i:4;i:282;}";'
views:
  - 1
categories:
  - Linux
---
每次在 [wine][1] 裡安裝程式, 需要另外安裝 dll 時, 都要上 google 找或是從另外一台 windows 機器複製過來嗎? vb6 runtime, msxml3 這些東西又在哪下載呢?

等等等, 救星來了! <a href="http://wiki.winehq.org/winetricks" target="_blank">winetricks</a> 這個小程式就可以自動安裝某些 dll 或函式庫.

### 安裝 winetricks

1.  首先下載 winetricks  
    > wget http://www.kegel.com/wine/winetricks

2.  改成可執行  
    > chmod +x winetricks

3.  看客官希望把程式放哪, 例如 ~/bin  
    > mv winetricks ~/bin/

### 使用 winetricks

*   列出 winetricks 使用方法及支援的套件  
    > winetricks &#8211;help

*   安裝套件  
    > winetricks < 套件名稱>
    
    例如安裝 VB6 runtime
    
    > winetricks vb6run

*   winetrick 有一個很\*簡陋\*的GUI (我寧可使用 cli 也不要用他的 gui )  
    > winetricks

也可以指定安裝的 wine 目錄, 例如

> env WINEPREFIX=~/.winetest winetricks mfc40

詳細說明請看 [winetricks 的說明頁][2].

 [1]: http://www.winehq.org/
 [2]: http://wiki.winehq.org/winetricks