---
title: scim 和 Firefox 在 ubuntu dapper 上的問題
author: TaopaiC
layout: post
permalink: /2006/04/08/130
tags:
  - 
wheredidtheycomefrom:
  - 's:72:"a:5:{i:0;i:131;i:1;s:3:"127";i:2;s:3:"190";i:3;s:3:"246";i:4;s:3:"201";}";'
  - 's:72:"a:5:{i:0;i:131;i:1;s:3:"127";i:2;s:3:"190";i:3;s:3:"246";i:4;s:3:"201";}";'
categories:
  - Linux
---
我的ubuntu有奇怪的問題, 在 gnome-terminal 可以正常使用/切換 scim , 但是在 Firefox 的視窗內, 就無法切換到 scim 的輸入法.  
<!--more-->

  
這個問題困腦了一兩個禮拜, 後來照著 [Yuren’s Info Area ? Blog Archive ? 咳… Ubuntu:][1] 的作法, 使用 m17n-env 設定 scim , 這個問題就時好時壞, 但至少可以 work &#8230;

但感覺上, ubuntu 是使用 im-switch , 應該不像以前那樣設定&#8230;  
( [imswitch-en][2] 不太確定是不是官方網頁 )

昨天找到一篇討論說可以試著移除掉 scim-pinyin , 就沒這個問題. 果然就解決了.. 但是 language-support-zh 需要 scim-pinyin , 我不想移除 language-support-zh &#8230;.

後來無意間發現在 /etc/X11/xinit/xinput.d 裡, 有個 zh\_TW 連結到 /etc/alternatives/xinput-zh\_TW , 而這個檔案又連結到 /etc/X11/xinit/xinput.d/scim-pinyin , 所以 zh\_TW 是設定成 scim 的拼音 (這個是zh\_CN用的吧?), 所以出現錯誤了&#8230; 後來把這個連結修正成 /etc/X11/xinit/xinput.d/scim-chewing 就<delete>解決</delete>了.

剛剛問學弟, 他說沒有這個問題, 看來 dapper flight 6 之後修正了吧? (我是在 dapper flight 5 裝的) <insert>註: 他沒裝 language-support-zh .</insert>

<insert>UPDATE: /etc/X11/xinit/xinput.d/ 下的 scim, scim-pinyin 和 scim-chewing 內容都差不多, 還是沒有解決問題&#8230; <img src='http://pctao.org/wp-includes/images/smilies/icon_neutral.gif' alt=':|' class='wp-smiley' />  
後來在另一台電腦上, 移除 scim-pinyin , 現在可以在 firefox 輸入中文..  
註: scim-pinyin 是 Language Support 安裝 language-support-zh 時安裝的&#8230; </insert>

 [1]: http://yurenju.info/?p=282
 [2]: http://kmuto.jp/open.cgi?imswitch-en&#038;l=en