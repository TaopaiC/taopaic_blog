---
title: '[小範例] 使用 Yahoo!生活+ API 與 Google Map'
author: TaopaiC
layout: post
permalink: /2008/01/24/213
wheredidtheycomefrom:
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
  - 's:56:"a:5:{i:0;i:225;i:1;i:234;i:2;i:218;i:3;i:215;i:4;i:214;}";'
pt_metakey_img:
  - 's:169:"a:3:{s:3:"img";s:57:"http://static.flickr.com/2119/2214423015_965b3184e1_m.jpg";s:3:"alt";s:0:"";s:3:"url";s:53:"http://www.flickr.com/photos/69004123@N00/2214423015/";}";'
categories:
  - Google
  - web
  - yahoo
---
[<img src="http://static.flickr.com/2119/2214423015_965b3184e1_m.jpg" align="right" border="0" />][1][小 YG 生活+][2] 的幕後&#8230;

[上上篇][3]講到Yahoo!生活+的API, 就拿來跟google map搞搞看, 弄了一個簡單的範例.  
除了[Y!生活+API][4]以外, 還用到<!--more-->

*   [Google Map API][5]: Google 地圖
*   [Google Custom Search Engine][6]: Google 提供可自訂的搜尋引擎
*   [Google AJAX Search][7]的Local Search. 已內含在 Google Map API 裡. 在google map裡顯示一個搜尋列,可以搜尋第圖上的資料.
*   [Yahoo Pipes][8],因為生活+提供的資料沒有[JSON][9]格式, 只好過水一下, 也順便擁有JSON+callback的能力.
*   [YUI 的 CSS 部份][10], 以及[Yullio][11].
*   [jQuery][12]

我將現在的程式碼以CC by-NC-SA的授權公開, 提供下載. 現在的程式碼並不複雜, 以後一些功能加上去, 反而不易閱讀. 也沒用到奇怪的技巧與技術, 希望能當作一個學習的範例.

**/\* 本篇只大概說明以及給相關連結, 並不是 step-by-step 文件. 網路上有太多教學文件了, 沒必要再造一個輪子.. \*/**

## Yahoo!生活+的部份

1.  首先要先申請 appid , 先到 [應用程式帳號申請][13] 填寫資料. 認證等級 (Authentication method) 選一般 (Generic) 即可. 接下來會獲得一組又臭又長的appid.
2.  再使用 Auth.bootUp 註冊 appid. 就可以使用 api 了.
3.  AJAX讀的資料無法跨站使用, 一個方法是用JSON+callback function (有專有名詞嗎?) , Yahoo Pipes 提供輸出成 json 格式, 以及加上 callback function. 只要先過Yahoo Pipes (可以使用[我做的][14]), 就有這好用功能. 請參閱[前篇][3].

## Google Map 的部份

1.  [Google Maps API Tutorial][15]: 很棒的教學與範例.
2.  [Google Earch Icons][16]: 列出 Google Earth 提供的icon
3.  列表上開啟marker: 有  
    > GEvent.trigger(marker, &#8220;click");
    
    可以用, 雖然每個教學都教你用
    
    > marker.openInfoWindowHtml(html[i]);

4.  [Info視窗最大化][17]: gmap官網提供的範例, 會有註冊複數個handler的問題, 我的方法是註冊一個, 每次查id . 請參閱程式碼.
5.  最大化Info視窗的內容:官網的範例是用 GDownloadUrl , 我的作法是先塞特定class的 <div>
      進去, 再讓callback function去更改內容.
    </div>

6.  [Local Search Control for Google Maps][18]

## jQuery:

1.  [隱藏詳細資料][19].
2.  處理url的query string: 用[Query String Object][20]這個plugin, 可以直接  
    > $.query.get(&#8216;classid&#8217;);
    
    取得 URL?classid=3 的classid的值.</li> 
    *   判斷導覽列上的標籤, 用 [getUrlParam][21] 取得 classid 的值, 再與現在的 classid 比對.</ol> 
    ## 程式碼
    
    下載程式碼看吧&#8230;  
    [程式碼][22] [測試網站][23] [目錄][24]

 [1]: http://www.flickr.com/photos/69004123@N00/2214423015/ "小 YG 生活+ - 咖啡簡餐"
 [2]: http://yg.goodstick.org/
 [3]: http://pctao.org/2008/01/23/214/
 [4]: http://tw.developer.yahoo.com/lifestyle.html
 [5]: http://code.google.com/apis/maps/
 [6]: http://www.google.com/coop/
 [7]: http://code.google.com/apis/ajaxsearch/
 [8]: http://pipes.yahoo.com/
 [9]: http://json.org/
 [10]: http://developer.yahoo.com/yui/grids/
 [11]: http://happydesigner.org/blog/2006/12/26/30
 [12]: http://jquery.com/
 [13]: https://developer.yahoo.com/wsregapp/index.php
 [14]: http://pipes.yahoo.com/pipes/pipe.info?_id=6d023b101b9afccd59ed9b284cbe54f3
 [15]: http://econym.googlepages.com/index.htm
 [16]: http://econym.googlepages.com/geicons.htm
 [17]: http://googlemapsapi.blogspot.com/2007/11/pump-up-your-info-windows-to-max.html
 [18]: http://www.google.com/uds/solutions/localsearch/index.html
 [19]: http://www.learningjquery.com/2008/01/revealing-details-with-jquery
 [20]: http://plugins.jquery.com/project/query-object
 [21]: http://plugins.jquery.com/project/getUrlParam
 [22]: http://page.goodstick.org/example/ylifestyle/map/source.zip
 [23]: http://page.goodstick.org/example/ylifestyle/map/example_1.html
 [24]: http://page.goodstick.org/example/ylifestyle/map/