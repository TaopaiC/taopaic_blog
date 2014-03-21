---
title: HTTP Redirect 和 URL Fragments
author: TaopaiC
layout: post
permalink: /2011/06/12/358
openid_comments:
  - 'a:1:{i:0;s:5:"19278";}'
categories:
  - web
---
最近在改 javascript 程式碼, 才注意到各家瀏覽器對 HTTP Redirect + URL Fragments 的行為不一樣.

規格書沒有規定瀏覽器要把 hash 的部份傳回伺服器 , 所以我們無法在 server 端接收到 `http://foo/#photo/bar` , 就直接在 Location 裡轉成 `http://foo/photo/#bar` , 因為伺服器端可能只收到 `http://foo/` . 這是題外話, 今天的重點不是這個.

今天討論的狀況比較簡單, 當使用者到 `http://foo/#photo/id` , 希望重導到某網頁, 所以伺服器端回應 HTTP 302 FOUND , 且 Location 欄位裡填上 `http://foo/bar/` 或是 `http://foo/bar/#picture` 時, 各家瀏覽器的行為不一樣.<!--more-->

查到[這篇][1] ([測試頁在此][2])把幾種瀏覽器都測過了, 節錄結果如下:

> 當 `http://foo/#Origin` -> `http://foo/bar/` 時
> 
> *   Firefox / Chrome / Opera / Firefox for Android 會導到 `http://foo/bar/#Origin`
> *   IE / Safari / Mobile Safari / Android 會導到 `http://foo/bar/`
> 
> 當 `http://foo/#Origin` -> `http://foo/bar/#New` 時
> 
> *   Firefox / Chrome / Opera 11.11+ / IE / Safari / Mobile Safari / Android / Firefox for Android 會導到 `http://foo/bar/#New`
> *   Opera 11.01- 會導到 `http://foo/bar/#Origin`
> 
> 註: 當 https < -> http , 或是 #! (hash bang) , 情況都同上. 

相關資料

*   [URL Fragments and Redirects &#8211; EricLaw&#8217;s IEInternals][1]
*   [httpstat.us][3]

 [1]: http://blogs.msdn.com/b/ieinternals/archive/2011/05/17/url-fragments-and-redirects-anchor-hash-missing.aspx
 [2]: https://www.fiddler2.com/test/redir/fragment/
 [3]: http://httpstat.us