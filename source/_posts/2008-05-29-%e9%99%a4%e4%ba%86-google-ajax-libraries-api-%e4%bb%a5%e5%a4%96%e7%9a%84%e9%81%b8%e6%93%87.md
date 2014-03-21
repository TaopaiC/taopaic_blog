---
title: 除了 Google AJAX Libraries API 以外的選擇
author: TaopaiC
layout: post
permalink: /2008/05/29/235
wheredidtheycomefrom:
  - 's:72:"a:5:{i:0;i:215;i:1;s:3:"232";i:2;s:3:"246";i:3;s:3:"236";i:4;s:3:"225";}";'
  - 's:72:"a:5:{i:0;i:215;i:1;s:3:"232";i:2;s:3:"246";i:3;s:3:"236";i:4;s:3:"225";}";'
  - 's:72:"a:5:{i:0;i:215;i:1;s:3:"232";i:2;s:3:"246";i:3;s:3:"236";i:4;s:3:"225";}";'
  - 's:72:"a:5:{i:0;i:215;i:1;s:3:"232";i:2;s:3:"246";i:3;s:3:"236";i:4;s:3:"225";}";'
views:
  - 1
categories:
  - javascript
  - web
---
[Google AJAX Libraries API][1] 提供幾個知名的 javascript 函式庫的 hosting, 但是 google 就沒有提供肥滋滋的 [ExtJS][2], 除此之外還有啥選擇呢?

如果你是使用&#8230;<!--more-->

### [YUI &#8211; The Yahoo! User Interface Library][3]

[官方就提供 CDN][4] 了..例如:  
`<script type="text/javascript" src="http://yui.yahooapis.com/2.5.1/build/yahoo/yahoo-min.js" ></script>`

### [DOJO][5]

AOL 有提供 [dojo 的 CDN][6] , 例如  
`<script type="text/javascript" src="http://o.aolcdn.com/dojo/1.1.1/dojo/dojo.xd.js"></script>`

### [JQuery][7]

官方有  
`<script type="text/javascript" src="http://code.jquery.com/jquery-latest.pack.js"></script>`  
或者是放於 [google code][8] 的  
`<script type="text/javascript" src="http://jqueryjs.googlecode.com/files/jquery-1.2.6.js"></script>`  
( <del datetime="2008-05-29T22:11:40+00:00">誰可以告訴我, 直接使用以上這兩個連結合法嗎?</del> )  
<ins datetime="2008-05-29T22:11:40+00:00">update: 有興趣可以看 <a href="http://blog.gslin.org/">gslin長輩</a> 提供的<a href="http://dean.edwards.name/weblog/2007/03/google-it/#comment84791">討論連結</a></ins>  
老實說, 這兩個比不上 Google AJAX lib API 提供的, 前者用 AmazonS3 只有 ETAG , 後者的過期時間才一個禮拜. 反正[很多人][9]使用放於 google code 的 jquery , 所以 google 乾脆把他變成官方服務吧..

### [cachefile.net][10]

這是本篇的主角, 在 google 之前就有好心人提供差不多的服務, cachefile 不只有[很多 js lib][11] , 還有[圖示][12]等等, 例如知名的 [famfamfam icon][13] 也有 ([在此][14]) . 使用方法就自行找該檔案連結, 例如:  
`<script type="text/javascript" src="http://cachefile.net/scripts/dojo/1.0.0/dojo/dojo.js"></script>`  
除此之外, 還可以自行控制過期時間  
`<script type="text/javascript" src="http://cachefile.net/scripts/dojo/1.0.0/dojo/dojo.js<br />
?expires=Thu,+01+Jan+2009+00:00:00+GMT"></script>`  
注意: 控制過期時間因為有 query string 所以**是不同的 URI , 無法享受到快取的優點**.

 [1]: http://pctao.org/2008/05/28/232/
 [2]: http://extjs.com/
 [3]: http://developer.yahoo.com/yui/
 [4]: http://developer.yahoo.com/yui/articles/hosting/
 [5]: http://dojotoolkit.org/
 [6]: http://dev.aol.com/dojo
 [7]: http://jquery.com/
 [8]: http://code.google.com/p/jqueryjs/downloads/list
 [9]: http://www.google.com.tw/search?q="http%3A%2F%2Fjqueryjs.googlecode.com%2Ffiles%2F"
 [10]: http://cachefile.net
 [11]: http://cachefile.net/scripts/
 [12]: http://cachefile.net/graphics/
 [13]: http://www.famfamfam.com/lab/icons/
 [14]: http://cachefile.net/graphics/ui/famfamfam/