---
title: '[From Digg] Open Letter to D-Link about their NTP vandalism'
author: TaopaiC
layout: post
permalink: /2006/04/08/131
tags:
  - 
wheredidtheycomefrom:
  - 's:30:"a:2:{i:0;i:132;i:1;s:3:"222";}";'
categories:
  - General
---
從 [digg][1] 看來的 : [Open Letter to D-Link about their NTP vandalism][2]

phk 寫給 DLINK 的公開信, 關於 DLINK 的網路設備錯誤的將 NTP 伺服器列表寫死在 firmware 裡, 這樣只有當使用者更新firmware時, 才有可能更新伺服器列表. phk 建議應該用 DNS record 紀錄伺服器列表, 如 ntp.dlink.com .  
NTP 一般不是公開給大家查詢時間的嗎? 問題在那? 問題在 GPS.dix.dk 的不是設置給一般 client 使用的. 而 DLINK 如此廣大的使用, 讓原本的<del> ISP </del> <insert>丹麥的交換中心</insert>要像 phk 收費了&#8230; XD  
<!--more-->

  
[NTP projects list of Stratum 1 NTP servers ][3]中是這個紀錄的

> DK Denmark GPS.dix.dk (192.38.7.240)  
> Location: Lyngby, Denmark  
> Geographic Coordinates: 55:47:03.36N, 12:03:21.48E  
> Synchronization: NTP V4 GPS with OCXO timebase  
> Service Area: Networks BGP-announced on the DIX  
> Access Policy: open access to servers, please, no client use  
> Contacts: Poul-Henning Kamp (phk@FreeBSD.org)  
> Note: timestamps better than +/-5 usec. 

在公開信的最後, phk 說這不是第一起相關事件, 之前的 [NetGear products blasted University of Wisconsin off the net][4] 迫使 NTP 通訊協定設計者加入 &#8220;kiss of death" 這個選項, phk也試過, 但是 DLINK 沒有照標準實做這個&#8230; XD

 [1]: http://www.digg.com
 [2]: http://digg.com/hardware/Open_Letter_to_D-Link_about_their_NTP_vandalism
 [3]: http://www.eecis.udel.edu/~mills/ntp/clock1a.html
 [4]: http://www.cs.wisc.edu/~plonka/netgear-sntp/