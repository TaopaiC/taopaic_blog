---
title: '[GPS] HOLUX M-241 在 ubuntu linux 上使用'
author: TaopaiC
layout: post
permalink: /2008/02/07/222
wheredidtheycomefrom:
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
  - 's:54:"a:5:{i:0;i:238;i:1;i:206;i:2;i:223;i:3;i:2;i:4;i:221;}";'
pt_metakey_img:
  - 's:169:"a:3:{s:3:"img";s:57:"http://static.flickr.com/2096/2237185357_0a1e121521_m.jpg";s:3:"alt";s:0:"";s:3:"url";s:53:"http://www.flickr.com/photos/69004123@N00/2237185357/";}";'
categories:
  - Linux
---
[<img src="http://static.flickr.com/2096/2237185357_0a1e121521_m.jpg" align="right" border="0" />][1]家人要出國玩, 我想他們帶 gps logger 出去紀錄路程, 回來做點不一樣的紀錄.  
我原本有個 [Wintec WBT-100][2] , 但有些缺點不太適合初學者帶出去, 尤其充電電池需帶充電器, 電池續航只有一天實在麻煩.  
我就再買一個 [HOLUX M-241][3] , 使用 AA 電池, 一顆可用一天, 有小螢幕, 中文選單. 其實相似產品還有 [Wintec WPL-1000][4]可以選, 但離出國時間緊迫, 以能馬上入手為優先, 最後就是買到這台 HOLUX M-241 .

還沒多少時間測試, 這篇主要介紹如何在 linux 上取出 gps logger 紀錄的資料.<!--more-->

用 USB 線連接電腦後, 開終端機 (terminal) 打 dmesg 看連到哪個埠

> [52244.118222] usb 5-5.4: new full speed USB device using ehci_hcd and address 10  
> [52244.216512] usb 5-5.4: configuration #1 chosen from 1 choice  
> [52244.216998] cp2101 5-5.4:1.0: cp2101 converter detected  
> [52244.297647] usb 5-5.4: reset full speed USB device using ehci_hcd and address 10  
> [52244.402412] usb 5-5.4: cp2101 converter now attached to **ttyUSB0**

以上的例子是連到 **/dev/ttyUSB0** .

### 用 wine 執行原廠的程式

[<img src="http://static.flickr.com/2143/2246852365_4124b6969a_m.jpg" align="right" border="0" />][5]首先製造 wine 的 com1 , 以剛剛連上 ttyUSB0 為例

> ln -s /dev/ttyUSB0 ~/.wine/dosdevices/com1

再執行 HoluxUtility 即可

> wine HoluxUtility.exe

使用會有點慢, 而且有時候程式會沒反應.

### BT747

或者用 [BT747][6] , 這軟體適用在 MTK GPS晶片的GPS裝置上, 當然 M-241 這台也行.  
先安裝 librxtx-java , 再執行 <http://bt747.sourceforge.net/BT747.jnlp> (Java Web Start) , 連線速度記得選 38440 , 再按 Connect Port 即可.

資料拿出來之後, 可以玩的就多了.. 例如[照片結合GPS資料][7].

(以下測試興奇購物網的廣告)  
[<img alt="HOLUX M-241無線GPS紀錄器 " src="http://partner.monday.com.tw/pub/gd.ashx?s=1&gdid=774004&mcode=MV9jWkhDUnNmbGxVa2NyU2tpMDlGa3ZnZWVKU0psU1VXNEV5d092ZVNEa0IwPQ==" border="0" height="240" width="210" />][8]

 [1]: http://www.flickr.com/photos/69004123@N00/2237185357/ "HOLUX M-241 GPS Logger"
 [2]: http://www.wintec.com.tw/GPS/bluetoothgps/WBT100.htm
 [3]: http://www.holux.com/JCoreTW/en/products/products_content.jsp?pno=340
 [4]: http://www.wintec.com.tw/b5/product_detail.php?pro_id=76%20style=
 [5]: http://www.flickr.com/photos/69004123@N00/2246852365/ "Screenshot-長天軌跡記錄器工具程式.png"
 [6]: http://bt747.wiki.sourceforge.net/
 [7]: http://pctao.org/2008/01/10/206/
 [8]: http://partner.monday.com.tw/pub/gotobuy.ashx?gdid=774004&mcode=MV9jWkhDUnNmbGxVa2NyU2tpMDlGa3ZnZWVKU0psU1VXNEV5d092ZVNEa0IwPQ==