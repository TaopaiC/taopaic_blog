---
title: '[fix] FeedJack 抓取 Yahoo! blog 的日期格式'
author: TaopaiC
layout: post
permalink: /2006/10/21/167
tags:
  - 
wheredidtheycomefrom:
  - 's:44:"a:3:{i:0;i:168;i:1;s:3:"139";i:2;s:3:"191";}";'
categories:
  - General
  - Software
---
最近用 [FeedJack][1] 架好一個 [planet][2] . 安裝的 step-by-step 過幾天有空再寫.  
試抓幾個 blog , 都很順利, 但是抓[學弟][3]在 [Yahoo!奇摩部落格 beta][4] 出現問題. 抓回來的時間不正確, 10/18 的文章變成 10/1 的文章.

仔細看 RSS 內容, 日期格式是這樣

> <pubDate>2006/10/20 00:29:09</pubDate>

和 [RSS v2 的規格書][5]不一樣, 要符合[RFC 822][6], 以wordpress產生為例

> <pubDate>Mon, 16 Oct 2006 18:13:48 +0000</pubDate>

用 [Feed validator][7] 檢查, 也是說日期欄位不對.

拜託學弟用 [Feed Burner][8] 燒燒看, 問題還是一樣.  
乾脆拜託學弟寄抱怨信給 Yahoo!奇摩. XD

問了 google , 果然也有人有[這個問題][9].<!--more-->

  
FeedJack 用來處理 feed 的 [FeedParser][10] 可以自己寫處理日期的 handler . 參考範例改的程式, 可以正確辨識日期.

> import feedparser  
> import re
> 
> \_my\_date_pattern = re.compile( \  
> r&#8217;(\d{,4})/(\d{,2})/(\d{2}) (\d{,2}):(\d{2}):(\d{2})&#8217;)
> 
> def myDateHandler(aDateString):  
> &#8220;""parse a UTC date in MM/DD/YYYY HH:MM:SS format"""  
> year, month, day, hour, minute, second = \  
> \_my\_date_pattern.search(aDateString).groups()  
> return (int(year), int(month), int(day), \  
> int(hour), int(minute), int(second), 0, 0, 0)
> 
> feedparser.registerDateHandler(myDateHandler)  
> d = feedparser.parse(&#8220;http://tw.myblog.yahoo.com/l314kimo/rss")  
> e = d.entries[0]  
> print e.updated  
> print e.updated_parsed

如果程式判斷的日期正確就成功了

> pctao@pcsh \[~/tmp\] \[4:23/W6\] python testfeed.py  
> 2006/10/21 01:22:32  
> (2006, 10, 21, 1, 22, 32, 0, 0, 0)

再去修改 feedjack_update.py , FreeBSD 是裝在

> /usr/local/lib/python2.4/site-packages/Feedjack-0.9.7-py2.4.egg/EGG-INFO/scripts/feedjack_update.py

現在 planet運作正常!

PS. 我還不會寫 python , 如果有錯歡迎指教.

 [1]: http://www.feedjack.org/
 [2]: http://planet.nccucs.org/
 [3]: http://tw.myblog.yahoo.com/l314kimo
 [4]: http://tw.blog.yahoo.com/
 [5]: http://blogs.law.harvard.edu/tech/rss
 [6]: http://asg.web.cmu.edu/rfc/rfc822.html
 [7]: http://feedvalidator.org/
 [8]: http://www.feedburner.com/
 [9]: http://www.archivesat.com/Planet_development_discussion_(and_user_support)/thread1752542.htm
 [10]: http://www.feedparser.org/