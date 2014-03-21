---
title: Google 與 Yahoo 提供 OpenID !!
author: TaopaiC
layout: post
permalink: /2008/01/21/210
wheredidtheycomefrom:
  - 's:64:"a:5:{i:0;i:212;i:1;i:144;i:2;i:214;i:3;s:3:"211";i:4;s:3:"209";}";'
pt_metakey_img:
  - 's:169:"a:3:{s:3:"img";s:57:"http://static.flickr.com/2004/2209186032_4de6635e4c_m.jpg";s:3:"alt";s:0:"";s:3:"url";s:53:"http://www.flickr.com/photos/69004123@N00/2209186032/";}";'
categories:
  - web
---
[<img src="http://static.flickr.com/2004/2209186032_4de6635e4c_m.jpg" align="right" border="0" />][1][][2][Google][3] 和 [Yahoo][4] 這幾天先後宣佈支援 [OpenID][5] ([維基百科][6])  
from [維基百科][6] 的解釋

> OpenID 是一個去中心化的單一登陸身份系統。對於支持OpenID的網站，用戶不需要記住像用戶名和密碼這樣的傳統驗證標記。取而代之的是，他們只需要預先在一個作為OpenID身份提供者(identity provider, IdP)的網站上註冊。

但現階段, Google 和 Yahoo 僅作為 OpenID 身份提供者, 只有 google blogger 的留言部份提供 別的OpenID 登入.<!--more-->

  
[Yahoo 的 OpenID][7] , 官網說 1/30 才開放. 使用 &#8220;yahoo.com" 就會帶你回 yahoo 做登入的動作.  
其實 1/8 時, 就[有人查覺 flickr 偷偷放上 openid 的 tag][8]  
:

> <link rel="openid2.provider" href="https://open.login.yahooapis.com/openid/op/auth" />
> 
到底會提供怎樣的服務, 1/30開放時就知道了.  
至於 Google 的 OpenID , 首先到 [draft.blogger.com][9] [開啟 OpenID 的功能.][10] 為何在 draft.blogger.com ? 沒錯, 這個功能還在測試.  
[][11][<img src="http://static.flickr.com/2113/2209166222_c1c4c2a460_d.jpg" border="0" />][11]  
開啟之後, 會發現你的 blogger 頁面原始碼多這行

> <link rel="openid.server" href="http://draft.blogger.com/openid-server.g" />
> 
就可以你的 blogger 的網址登入了.  
以 blogger 的留言為例 , 選 Any OpenID , 鍵入網址,  
[<img src="http://static.flickr.com/2219/2209166336_17702c7247_m.jpg" border="0" />][12]  
就會帶你去 blogger 的頁面.  
[<img src="http://static.flickr.com/2108/2208370481_4536e456dd_m.jpg" border="0" />][13]  
可以選擇一次或永遠, 這樣就完成 OpenID 的登入.  
我開了一篇測試文章, 歡迎到[這篇][14]測試OpenID的登入與留言.

 [1]: http://www.flickr.com/photos/69004123@N00/2209186032/ "OpenID logo"
 [2]: http://www.flickr.com/photos/69004123@N00/2209179010/ "OpenID logo"
 [3]: http://bloggerindraft.blogspot.com/2008/01/new-feature-blogger-as-openid-provider.html
 [4]: http://yhoo.client.shareholder.com/press/releasedetail.cfm?ReleaseID=287698
 [5]: http://openid.net/
 [6]: http://zh.wikipedia.org/wiki/OpenID
 [7]: http://openid.yahoo.com/
 [8]: http://www.readwriteweb.com/archives/flickr_to_authenticate_openid.php
 [9]: http://draft.blogger.com/
 [10]: http://draft.blogger.com/edit-profile.g
 [11]: http://www.flickr.com/photos/69004123@N00/2209166222/ "Blogger in draft: Edit User Profile"
 [12]: http://www.flickr.com/photos/69004123@N00/2209166336/ "blogger open comment"
 [13]: http://www.flickr.com/photos/69004123@N00/2208370481/ "Google Blogger OpenID"
 [14]: http://taopaictest.blogspot.com/2008/01/openid-test.html