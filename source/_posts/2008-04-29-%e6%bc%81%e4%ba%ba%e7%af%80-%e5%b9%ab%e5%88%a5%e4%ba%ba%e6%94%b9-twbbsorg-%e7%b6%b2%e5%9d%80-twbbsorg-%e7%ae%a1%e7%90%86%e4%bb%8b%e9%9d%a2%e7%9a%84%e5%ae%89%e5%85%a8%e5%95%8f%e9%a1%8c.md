---
title: '[漁人節?] 幫別人改 twbbs.org 網址- twbbs.org 管理介面的安全問題'
author: TaopaiC
layout: post
permalink: /2008/04/29/228
wheredidtheycomefrom:
  - 's:75:"a:5:{i:0;s:2:"22";i:1;s:3:"245";i:2;s:3:"230";i:3;s:3:"221";i:4;s:3:"229";}";'
  - 's:75:"a:5:{i:0;s:2:"22";i:1;s:3:"245";i:2;s:3:"230";i:3;s:3:"221";i:4;s:3:"229";}";'
  - 's:75:"a:5:{i:0;s:2:"22";i:1;s:3:"245";i:2;s:3:"230";i:3;s:3:"221";i:4;s:3:"229";}";'
pt_metakey_img:
  - 's:185:"a:3:{s:3:"img";s:63:"http://farm3.static.flickr.com/2079/2451316007_cdc3b8d0ca_m.jpg";s:3:"alt";s:14:"ptt or 無名?";s:3:"url";s:48:"http://www.flickr.com/photos/taopaic/2451316007/";}";'
categories:
  - web
---
應該只有愚人節才會看到bbs站互調, 但是今天 wretch.twbbs.org (應該是[無名bbs][1]用的網址) 變成 ptt 的 ip 了  
[<img src="http://farm3.static.flickr.com/2079/2451316007_cdc3b8d0ca_m.jpg" alt="ptt or 無名?" width="240" height="189" />][2]

**我並沒有刻意研究hack/crack相關技術, 可是這個洞實在太明顯了, 誰都看的到吧&#8230;**

兩個小時前已經寄信給 [twbbs.org][3] 的管理者希望他們能修正, 我原本打算等到漏洞補起來再來寫blog, 但現在[看到 wretch.twbbs.org 的 ip 被改掉][4] (當然不是我動的, 其他網路高手搶先一步..), 應該可以寫了吧&#8230;

至於方法, 當然只能等漏洞修正以後再貼了&#8230; *update: 官方已修正, 所以方法請看[這篇part 2][5]  
影響層面, 轉址問題還小, 大家還記得 [Group.nctu.edu.tw 的轉信服務][6]的話, 如果有站台偽裝成別站的話, 就能收到該站的轉信&#8230; 其中或許包含隱版. 例如廣大的 ptt2 的個人看板..

<!--more-->

  
以下是ip查詢資料

> pctao@pctao-desktop:~$ dig -t NS twbbs.org
> 
> ; <<>> DiG 9.4.2 <<>> -t NS twbbs.org  
> ;; global options: printcmd  
> ;; Got answer:  
> ;; ->>HEADER<<- opcode: QUERY, status: NOERROR, id: 57972  
> ;; flags: qr rd ra; QUERY: 1, ANSWER: 4, AUTHORITY: 0, ADDITIONAL: 4
> 
> ;; QUESTION SECTION:  
> ;twbbs.org. IN NS
> 
> ;; ANSWER SECTION:  
> twbbs.org. 52195 IN NS dns02.twbbs.org.  
> twbbs.org. 52195 IN NS dns01.twbbs.org.  
> twbbs.org. 52195 IN NS dns04.twbbs.org.  
> twbbs.org. 52195 IN NS dns03.twbbs.org.
> 
> ;; ADDITIONAL SECTION:  
> dns02.twbbs.org. 54943 IN A 67.228.195.210  
> dns01.twbbs.org. 45787 IN A 203.67.71.132  
> dns04.twbbs.org. 54943 IN A 61.30.235.34  
> dns03.twbbs.org. 47287 IN A 64.34.197.175
> 
> ;; Query time: 45 msec  
> ;; SERVER: 127.0.0.1#53(127.0.0.1)  
> ;; WHEN: Tue Apr 29 21:48:34 2008  
> ;; MSG SIZE rcvd: 171
> 
> pctao@pctao-desktop:~$ nslookup wretch.twbbs.org dns01.twbbs.org  
> Server: dns01.twbbs.org  
> Address: 203.67.71.132#53
> 
> Name: wretch.twbbs.org  
> Address: 140.112.172.11
> 
> pctao@pctao-desktop:~$ nslookup ptt.twbbs.org dns01.twbbs.org  
> Server: dns01.twbbs.org  
> Address: 203.67.71.132#53
> 
> Name: ptt.twbbs.org  
> Address: 140.112.172.11

 [1]: telnet://wretch.twbbs.org
 [2]: http://www.flickr.com/photos/taopaic/2451316007/ "ptt or 無名? by TaopaiC, on Flickr"
 [3]: http://twbbs.org
 [4]: http://www.ptt.cc/bbs/Gossiping/M.1209475071.A.41E.html
 [5]: http://pctao.org/2008/04/30/230/
 [6]: http://group.nctu.edu.tw/