---
title: Google 幫忙 host 幾個知名 JavaScript 函式庫
author: TaopaiC
layout: post
permalink: /2008/05/28/232
wheredidtheycomefrom:
  - 's:56:"a:5:{i:0;i:258;i:1;i:235;i:2;i:233;i:3;i:213;i:4;i:225;}";'
  - 's:56:"a:5:{i:0;i:258;i:1;i:235;i:2;i:233;i:3;i:213;i:4;i:225;}";'
categories:
  - Google
  - javascript
  - web
---
剛看到 [google 推出 AJAX Libraries API][1] , 實際上就是 google host 幾個知名的 JavaScript 函式庫, 包含:

*   JQuery
*   prototype
*   script.aculo.us
*   MooTools
*   dojo

通常網站會將不常更動的函式庫做 gzip (壓縮) 和 cache (快取) , 以節省訪客再次造訪的流量 (這裡和之後指的流量為該函式庫的流量), 但首次訪客還是要下載一次. 如果使用這個服務的話, 該訪客在其他也使用的網站下載過該函式庫, 就不需要下載第二次, 節省流量和增快開啟網頁的速度. 對網站主而言, 省了首次訪客的流量, 對使用者來說, 省了 n 個網站的流量. 聽起來真不錯.<!--more-->

使用方法也很簡單, 第一種直接使用  
`<script src="http://ajax.googleapis.com/ajax/libs/prototype/1.6.0.2/prototype.js"></script>`  
其他版本或函式庫的位置請查[官網說明][2]

第二種使用 google.load() 的方式,  
`<script src="http://www.google.com/jsapi"></script> <script type="text/javascript"><!--<br />
google.load("jquery", "1.2.3");<br />
google.setOnLoadCallback(function() {<br />
// init function...<br />
});<br />
// --><br />
</script><br />
`  
如果要未壓縮過的版本,  
`google.load("jquery", "1.2.3", {uncompressed:true});`  
google.load() 有自動版本的功能, 例如 1.2 則自動幫你找 1.2.X 的最高版本. 請見[官網說明][3]

### 相關連結

*   [AJAX Libraries API][4] &#8211; 本次主角的說明文件
*   [Google&#8217;s AJAX APIs Document][5] &#8211; google.load 的說明文件
*   [Ajaxian » Announcing AJAX Libraries API: Speed up your Ajax apps with Google’s infrastructure][6] &#8211; [Dion Almaer][7] (AJAX Libraries API作者) 對於 AJAX lib API 的介紹

 [1]: http://googleajaxsearchapi.blogspot.com/2008/05/speed-up-access-to-your-favorite.html
 [2]: http://code.google.com/apis/ajaxlibs/documentation/index.html
 [3]: http://code.google.com/apis/ajax/documentation/#Versioning
 [4]: http://code.google.com/apis/ajaxlibs/
 [5]: http://code.google.com/apis/ajax/documentation/
 [6]: http://ajaxian.com/archives/announcing-ajax-libraries-api-speed-up-your-ajax-apps-with-googles-infrastructure
 [7]: http://ajaxian.com/about-us/#DionAlmaer