---
title: '[GMap] 新功能 &#8211; 靜態地圖 &#8211; 不需 javascript 顯示地圖 (Google Static Maps)'
author: TaopaiC
layout: post
permalink: /2008/02/22/225
wheredidtheycomefrom:
  - 's:56:"a:5:{i:0;i:227;i:1;i:235;i:2;i:232;i:3;i:234;i:4;i:224;}";'
  - 's:56:"a:5:{i:0;i:227;i:1;i:235;i:2;i:232;i:3;i:234;i:4;i:224;}";'
  - 's:56:"a:5:{i:0;i:227;i:1;i:235;i:2;i:232;i:3;i:234;i:4;i:224;}";'
pt_metakey_img:
  - 's:169:"a:3:{s:3:"img";s:57:"http://static.flickr.com/2020/2282368693_89bb37575a_m.jpg";s:3:"alt";s:0:"";s:3:"url";s:53:"http://www.flickr.com/photos/69004123@N00/2282368693/";}";'
categories:
  - Google
---
Google 新增 static maps (中文該怎麼翻? 靜態地圖?) 的功能, 可以直接取得以圖片形式呈現的地圖, 相對於 Google Map 的 [javascript api][1] 或讓人[直接貼在網頁上顯示的方式(Embeddable Maps)][2], 省去了 script loading , 較輕且較快.  
例如: ([連結][3])  
`http://maps.google.com/staticmap?<br />
center=24.987108287597472,121.57406330108643&<br />
markers=24.987186084753883,121.57354831695557,red&<br />
zoom=15&size=300x200&<br />
key=ABQIAAAABPwouWYj3VnD5GFB6ruqxxRQKVdcuJ1PIKoX_YH_iOiTm<br />
ZiR8BR__D2FH9CJzfKzbgyDU3EOrVPL8w`  
即可產生  
[<img border="0" src="http://static.flickr.com/2020/2282368693_89bb37575a_m.jpg" />][4]  
(此圖為另存於flickr的圖)

有什麼用呢?<!--more-->

  
可直接另存圖片再寄給朋友, 或者製作混撘 (mashup) 程式時, 不必產生多個 js 地圖. ([類似應用的範例][5])

Google 也製作一個簡易的 **[精靈][6]** 幫助產生 static map . 如果要直接貼於網頁上的話, 需跟google其他服務一樣申請 API KEY, 精靈最下方的 Site URL 欄位填上要貼上網站的網址, 例如: `http://pctao.org/` , 再按 **Generate Key** 產生該站專屬的 API KEY . 注意: 此 API KEY 貼在其他網頁就看不到該圖.

詳細的用法請參閱 [文件][7] , 精靈未提供 [maptype][8] (roadmap 與 mobile ) 或 [多個marker][9] 的功能, 就請參閱文件了.

後記: 其實前幾天查 [google ajax search][10] 時, 就有發現類似的功能, local search 的結果都有包含 staticMapUrl 的屬性, 也是一張靜態地圖, [官方範例][5].  
[<img border="0" src="http://static.flickr.com/2249/2283201592_a665c2415f_m.jpg" />][11]

相關連結

*   [Google Static Maps 產生精靈][6]
*   [Google Static Maps API 文件][7]
*   [Google Maps Without the Scripting][12] (Google Map API 官方 blog)
*   [ajax search example: Static Map Images][5]

 [1]: http://code.google.com/apis/maps/
 [2]: http://googlemapsapi.blogspot.com/2007/08/dont-feel-like-coding-embed-map.html
 [3]: http://maps.google.com/staticmap?center=24.987108287597472,121.57406330108643&markers=24.987186084753883,121.57354831695557,red&zoom=15&size=300x200&key=ABQIAAAABPwouWYj3VnD5GFB6ruqxxRQKVdcuJ1PIKoX_YH_iOiTmZiR8BR__D2FH9CJzfKzbgyDU3EOrVPL8w
 [4]: http://www.flickr.com/photos/69004123@N00/2282368693/ "NCCU (google static maps)"
 [5]: http://www.google.com/uds/samples/apidocs/static-tiles.html
 [6]: http://gmaps-samples.googlecode.com/svn/trunk/simplewizard/makestaticmap.html
 [7]: http://code.google.com/apis/maps/documentation/staticmaps/index.html
 [8]: http://code.google.com/apis/maps/documentation/staticmaps/index.html#MapTypes
 [9]: http://code.google.com/apis/maps/documentation/staticmaps/index.html#Markers
 [10]: http://code.google.com/apis/ajaxsearch/
 [11]: http://www.flickr.com/photos/69004123@N00/2283201592/ "Screenshot-Static Map Tiles - Google AJAX Search API demo.png"
 [12]: http://googlemapsapi.blogspot.com/2008/02/google-maps-without-scripting.html