---
title: '[wordpress] Google AJAX Libraries API Plugin'
author: TaopaiC
layout: post
permalink: /2008/05/30/236
wheredidtheycomefrom:
  - 's:62:"a:5:{i:0;i:234;i:1;i:2;i:2;i:208;i:3;s:3:"237";i:4;s:3:"232";}";'
views:
  - 1
categories:
  - Google
  - javascript
  - WordPress
---
前幾天 [Google 提供幾個知名 javascript 函式庫的hosting][1], 就想到 wordpress blog 能不能也利用該服務, 好歹可以省掉 jquery (30K) 和 prototype (124K) 的流量, 尤其是放在(暴)慢的主機 ( 如 dreamhoXt &#8230; ) 效果非常明顯&#8230;  
用 google 找到 [Google AJAX Libraries API Plugin][2] , <del datetime="2008-06-03T23:55:51+00:00">可惜有些問題, 寄修改檔給作者, 希望下一個版本能修正.</del><ins datetime="2008-06-03T23:55:51+00:00">作者已於0.6版本修正, 請至<a href="http://blog.clearskys.net/2008/05/28/google-ajax-libraries-api-plugin/">該作者網頁下載</a>.</ins>

==== GEEK 分隔線 ====  
<ins datetime="2008-06-03T23:55:51+00:00"><strong>UPDATE: v0.6已修正</strong></ins>  
該 plugin 沒寫授權方法, 所以我不好意思直接修改放出&#8230;  
wordpress 用的是加上 jQuery.noConflict() 的 jquery , 而 google 提供的沒有, 以至於直接使用 google 的 jquery 會[導致和 prototype 衝突][3]. 我的修改方式是在 jquery script 之後, 再加入一個內容為 jQuery.noConflict() 的 script .<!--more-->

在 usegooglelibrary.php (0.5版本) 加入  
`function gs_add_jquery_noconflict( $js_array ) {<br />
if ( FALSE !== $jquery = array_search( 'jquery', $js_array ) ) {<br />
wp_register_script('jquery_noconflict', '/wp-content/plugins/j.js', array('jquery'), null);<br />
array_splice( $js_array, $jquery+1, 0, 'jquery_noconflict' );<br />
}<br />
return $js_array;<br />
}<br />
add_filter('print_scripts_array', 'gs_add_jquery_noconflict');`  
以及在 wp-content/plugins 裡新增一個名為 j.js 的檔案, 內容為  
`jQuery.noConflict();`  
就會在載入 jquery 之後, 載入 j.js . 且不會和 prototype 衝突. 效果請看[筆者 blog][4] 的原始碼. 有錯誤/建議歡迎指教.

 [1]: http://pctao.org/2008/05/28/232/
 [2]: http://blog.clearskys.net/2008/05/28/google-ajax-libraries-api-plugin/
 [3]: http://docs.jquery.com/Using_jQuery_with_Other_Libraries
 [4]: http://pctao.org