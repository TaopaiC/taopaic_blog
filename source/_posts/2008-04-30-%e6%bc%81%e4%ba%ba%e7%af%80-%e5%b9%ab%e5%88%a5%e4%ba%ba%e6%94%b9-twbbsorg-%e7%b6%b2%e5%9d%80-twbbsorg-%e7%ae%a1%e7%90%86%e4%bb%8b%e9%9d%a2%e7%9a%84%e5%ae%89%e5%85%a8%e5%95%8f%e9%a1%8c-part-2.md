---
title: '[漁人節?] 幫別人改 twbbs.org 網址- twbbs.org 管理介面的安全問題 part 2'
author: TaopaiC
layout: post
permalink: /2008/04/30/230
wheredidtheycomefrom:
  - 's:72:"a:5:{i:0;i:231;i:1;s:3:"229";i:2;s:3:"228";i:3;s:3:"232";i:4;s:3:"241";}";'
  - 's:72:"a:5:{i:0;i:231;i:1;s:3:"229";i:2;s:3:"228";i:3;s:3:"232";i:4;s:3:"241";}";'
  - 's:72:"a:5:{i:0;i:231;i:1;s:3:"229";i:2;s:3:"228";i:3;s:3:"232";i:4;s:3:"241";}";'
pt_metakey_img:
  - 's:244:"a:3:{s:3:"img";s:63:"http://farm3.static.flickr.com/2372/2451273871_d4feff7233_m.jpg";s:3:"alt";s:68:"Screenshot-設定‧修改 網域 | TWBBS.org 自由網域 - Flock-1";s:3:"url";s:53:"http://www.flickr.com/photos/69004123@N00/2451273871/";}";'
categories:
  - web
---
**聲明:我並沒有刻意研究hack/crack相關技術, 這個洞實在太明顯, 我只是不小心看到而已…**

twbbs.org 的管理者回信說**已把該 bug 修正**了, 那我就可以繼續[上篇未寫完的部份][1]了.

這個 bug 在&#8230; 修正網址設定時, 依靠的是

`<input type="hidden" value="..." name="bbs_host"/>`

只要將 value 的值改成其他站台, 就可以幫其他人修正了, 離譜的是後台收到資料, 並沒有核對該網址是否有權限修改, so&#8230;

### 改 value="godstick"

<a class="flickr-image" title="改 value=godstick" rel="flickr-mgr" href="http://www.flickr.com/photos/69004123@N00/2451273871/"><img class="flickr-medium" longdesc="http://farm3.static.flickr.com/2372/2451273871_d4feff7233_s.jpg" src="http://farm3.static.flickr.com/2372/2451273871_d4feff7233_m.jpg" alt="Screenshot-設定‧修改 網域 | TWBBS.org 自由網域 - Flock-1" /></a>

詳細的就請自行看圖吧<!--more-->

### 帳號 TaopaiC , 擁有網址 goodstick.twbbs.org

<a class="flickr-image" title="帳號 TaopaiC , 擁有網址 goodstick.twbbs.org" rel="flickr-mgr[photo]" href="http://www.flickr.com/photos/69004123@N00/2451273435/"><img class="flickr-large" longdesc="http://farm3.static.flickr.com/2419/2451273435_cd0864ee54_s.jpg" src="http://farm3.static.flickr.com/2419/2451273435_cd0864ee54_m.jpg" alt="設定‧修改 網域 | TWBBS.org 自由網域_1209474179924" /></a>

### 帳號 REGex , 擁有網址 godstick.twbbs.org

<a class="flickr-image" title="帳號 REGex , 擁有網址 godstick.twbbs.org" rel="flickr-mgr[photo]" href="http://www.flickr.com/photos/69004123@N00/2452099026/"><img class="flickr-large" longdesc="http://farm4.static.flickr.com/3156/2452099026_fceb2c285b_s.jpg" src="http://farm4.static.flickr.com/3156/2452099026_fceb2c285b_m.jpg" alt="設定‧修改 網域 | TWBBS.org 自由網域_1209474283909" /></a>

### 這個是失誤.. 改 value 沒想到改成沒改 (原先goodstick , 改成 goodstick)&#8230;

<a class="flickr-image" title="這個是失誤.. 改 value 沒想到改成沒改" rel="flickr-mgr[photo]" href="http://www.flickr.com/photos/69004123@N00/2452099210/"><img class="flickr-medium" longdesc="http://farm4.static.flickr.com/3195/2452099210_3783645814_s.jpg" src="http://farm4.static.flickr.com/3195/2452099210_3783645814_m.jpg" alt="Screenshot-設定‧修改 網域 | TWBBS.org 自由網域 - Flock" /></a>

### 改 value="godstick"

<a class="flickr-image" title="改 value=godstick" rel="flickr-mgr[photo]" href="http://www.flickr.com/photos/69004123@N00/2451273871/"><img class="flickr-medium" longdesc="http://farm3.static.flickr.com/2372/2451273871_d4feff7233_s.jpg" src="http://farm3.static.flickr.com/2372/2451273871_d4feff7233_m.jpg" alt="Screenshot-設定‧修改 網域 | TWBBS.org 自由網域 - Flock-1" /></a>

### 帳號 TaopaiC , 顯示 godstick.twbbs.org 已被修改

<a class="flickr-image" title="帳號 TaopaiC , 顯示 godstick.twbbs.org 已被修改" rel="flickr-mgr[photo]" href="http://www.flickr.com/photos/69004123@N00/2452099490/"><img class="flickr-large" longdesc="http://farm3.static.flickr.com/2357/2452099490_b64216838a_s.jpg" src="http://farm3.static.flickr.com/2357/2452099490_b64216838a_m.jpg" alt="設定‧修改 網域 | TWBBS.org 自由網域_1209474697013" /></a>

### 帳號 Regex , godstick.twbbs.org 已被修改

<a class="flickr-image" title="帳號 Regex , godstick.twbbs.org 已被修改" rel="flickr-mgr[photo]" href="http://www.flickr.com/photos/69004123@N00/2451274123/"><img class="flickr-large" longdesc="http://farm3.static.flickr.com/2378/2451274123_bd276b0c45_s.jpg" src="http://farm3.static.flickr.com/2378/2451274123_bd276b0c45_m.jpg" alt="設定‧修改 網域 | TWBBS.org 自由網域_1209475430848" /></a>

 [1]: http://pctao.org/2008/04/29/228/