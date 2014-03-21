---
title: jQuery XSS with $(location.hash)
author: TaopaiC
layout: post
permalink: /2011/06/06/345
categories:
  - javascript
---
從 twitter 上看到 [new XSS pattern with jQuery][1] , 

<pre class="brush: jscript; title: ; notranslate" title="">http://ma.la/jquery_xss/#&lt;img src=/ onerror=alert(1)&gt;
</pre>

原因是 jQuery 對以下三種狀況的處理:

1.  `$("#id")` 是個 css selector
2.  `$("<img />")` 是 createElement
3.  `$("#<img />")` 也是 createElement

所以如果直接使用 `$(location.hash)` , 而 `location.hash` 是 `"#<img  onerror=.....>"` 的話, 就出意外啦.

`$(location.hash)` 哪裡會用呢? 像是用 ajax 做多頁啦, tab 啦&#8230; 像是 [jQuery mobile][2] 就中獎了 XDXD

 [1]: http://ma.la/jquery_xss/
 [2]: http://jquerymobile.com/