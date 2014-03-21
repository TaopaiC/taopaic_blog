---
title: Yahoo!生活+ API 簡單說明
author: TaopaiC
layout: post
permalink: /2008/01/23/214
wheredidtheycomefrom:
  - 's:76:"a:5:{i:0;s:3:"212";i:1;s:3:"215";i:2;s:3:"213";i:3;s:3:"101";i:4;s:3:"232";}";'
  - 's:76:"a:5:{i:0;s:3:"212";i:1;s:3:"215";i:2;s:3:"213";i:3;s:3:"101";i:4;s:3:"232";}";'
  - 's:76:"a:5:{i:0;s:3:"212";i:1;s:3:"215";i:2;s:3:"213";i:3;s:3:"101";i:4;s:3:"232";}";'
  - 's:76:"a:5:{i:0;s:3:"212";i:1;s:3:"215";i:2;s:3:"213";i:3;s:3:"101";i:4;s:3:"232";}";'
  - 's:76:"a:5:{i:0;s:3:"212";i:1;s:3:"215";i:2;s:3:"213";i:3;s:3:"101";i:4;s:3:"232";}";'
  - 's:76:"a:5:{i:0;s:3:"212";i:1;s:3:"215";i:2;s:3:"213";i:3;s:3:"101";i:4;s:3:"232";}";'
  - 's:76:"a:5:{i:0;s:3:"212";i:1;s:3:"215";i:2;s:3:"213";i:3;s:3:"101";i:4;s:3:"232";}";'
pt_metakey_img:
  - 's:169:"a:3:{s:3:"img";s:57:"http://static.flickr.com/2389/2211295731_fac582676c_m.jpg";s:3:"alt";s:0:"";s:3:"url";s:53:"http://www.flickr.com/photos/69004123@N00/2211295731/";}";'
categories:
  - web
---
[<img src="http://static.flickr.com/2389/2211295731_fac582676c_m.jpg" align="right" border="0" />][1]看了一下 [Y!生活+ 的API說明網頁][2], 一時還真摸不到頭緒. 乾脆寫下來紀錄一下.  
1. 首要要取得 appid , 在 [應用程式帳號申請][3] , 取得之後, 再連到 http://APIServer/version/Auth.bootUp?appid=$appid 啟動 appid . 例如現在 0.1 版本: ($appid請換成剛取得的appid)

> http://tw.lifestyle.yahooapis.com/v0.1/Auth.bootUp?appid=$appid

<!--more-->

  
2. 每個指令大概說明一下用法, 以 Biz.getDetails 為例, 可以帶一個 ID 參數, 連到

> http://tw.lifestyle.yahooapis.com/v0.1/Biz.getDetails?appid=$appid&ID=688a2dcbc5868c98

就可以取得結果. 注意: 每次都要帶 appid=$appid 的參數.[<img src="http://static.flickr.com/2392/2212019693_33af6c11e8_m.jpg" align="right" border="0" />][4]  
詳細說明就看官網吧.  
3. Biz.addReview , User.listBookmarks , Bookmark.listBizs 都會 403 Forbidden , 我猜要用 [BB Auth][5] 過才能使用.  
4. 商家的 ID 與 http://tw.lifestyle.yahoo.com/biz.html?bizid= 同, 如 ID 為 9b6e890a5ac3835b 的 [MK麻辣火鍋][6]  
, 網址為

> http://tw.lifestyle.yahoo.com/biz.html?bizid=9b6e890a5ac3835b

類別的 id 與 http://tw.lifestyle.yahoo.com/directory.html?sid= 同, 如 id 為 152959608 的 [川菜.麻辣火鍋][7] , 網址為

> http://tw.lifestyle.yahoo.com/directory.html?sid=152959608

5. 提醒:

*   lon 與 lng : Class.listBizsInRange 的參數是 lat 和 **lon** , 而不是 Google map 或 Urmap 習慣用的 lat 和 **lng** .
*   id 與 ID : 只有 Class.listClasses 是用 id 其他都是用 ID .

[<img src="http://static.flickr.com/2280/2212809262_0a22ebafea_m.jpg" align="right" border="0" />][8]6. 只有 xml , 沒有 json 支援..  
翻桌啊.. 這樣就非得要做 proxy 才能用..  
所以我做了一個 [Yahoo! Pipe][9] , 使用時, 加上 **&_render=json** 即為 json 輸出為格式, 再加上 **&_callback=cb** 即使用 cb 作為 callback function .  
參數的話, 請自行加上原本 API 的參數, fun 為使用的指令, 當然, appid 也要加上.  
例如原本

> http://tw.lifestyle.yahooapis.com/v0.1/Biz.getDetails?appid=$appid&ID=688a2dcbc5868c98

就變成

> http://pipes.yahoo.com/pipes/pipe.run?\_id=6d023b101b9afccd59ed9b284cbe54f3&version=v0.1&appid=$appid&fun=Biz.getDetails&ID=688a2dcbc5868c98&\_render=json&_callback=cb

 [1]: http://www.flickr.com/photos/69004123@N00/2211295731/ "YDN TW logo"
 [2]: http://tw.developer.yahoo.com/lifestyle_api.html
 [3]: https://developer.yahoo.com/wsregapp/index.php
 [4]: http://www.flickr.com/photos/69004123@N00/2212019693/ "Y!生活+ 的 API"
 [5]: http://tw.developer.yahoo.com/auth.html
 [6]: http://tw.lifestyle.yahoo.com/biz.html?bizid=9b6e890a5ac3835b
 [7]: http://tw.lifestyle.yahoo.com/directory.html?sid=152959608
 [8]: http://www.flickr.com/photos/69004123@N00/2212809262/ "Yahoo! Pipes"
 [9]: http://pipes.yahoo.com/pipes/pipe.info?_id=6d023b101b9afccd59ed9b284cbe54f3