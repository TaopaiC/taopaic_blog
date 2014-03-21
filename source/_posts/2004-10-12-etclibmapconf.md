---
title: /etc/libmap.conf
author: TaopaiC
layout: post
permalink: /2004/10/12/16
wheredidtheycomefrom:
  - 's:32:"a:2:{i:0;s:2:"12";i:1;s:2:"19";}";'
categories:
  - FreeBSD
---
前一篇[PACKAGESITE+pkg_add -rv][1]的方法, 在使用 &#8220;Packages from latest run on 5-current" 失算了, 因為 FreeBSD current 的 library 版本增加了.

不知道用 /etc/libmap.conf 硬幹, 可不可以用. 不然就真的要慢慢編了.

<!--more-->

  
/usr/ports/UPDATING 是這麼說的:

<blockquote title="/usr/ports/UPDATING">
  <p>
    20041001:<br /> AFFECTS: users of ports that require several base system libraries who<br /> are running FreeBSD 5.3-BETA7 or later (including -current)<br /> AUTHOR: kensmith@freebsd.org
  </p>
  
  <p>
    As part of the FreeBSD-5.3 release the following system libraries<br /> had their version number incremented:
  </p>
  
  <p>
    /lib/libm.so.2 -> libm.so.3<br /> /lib/libreadline.so.4 -> libreadline.so.5<br /> /usr/lib/libhistory.so.4 -> libhistory.so.5<br /> /usr/lib/libopie.so.2 -> libopie.so.3<br /> /usr/lib/libpcap.so.2 -> libpcap.so.3
  </p>
  
  <p>
    This should have no effect unless you are using FreeBSD 5.3-BETA7 or<br /> higher, or if you are a -current user who upgraded after this date.<br /> Assuming you did a from-source upgrade new versions of these libraries<br /> will be created but the old versions will be left behind (for example<br /> /lib/libm.so.2 will be the old one, /lib/libm.so.3 will be the new one).<br /> Any ports or pre-built packages you have currently installed will<br /> continue to use the old library, any ports you install after the upgrade<br /> will begin to use the new library. You will need to have all your<br /> ports recompiled before the old library goes away. To help with the<br /> migration you could also use /etc/libmap.conf to map libm.so.2 to<br /> libm.so.3.
  </p>
</blockquote>

Reference:

*   [HEADS-UP: Library versions have been bumped][2] 
    http://lists.freebsd.org/pipermail/freebsd-current/2004-October/039086.html
    
    Ken Smith kensmith at cse.Buffalo.EDU  
    Fri Oct 1 08:49:37 PDT 2004</li> </ul>

 [1]: http://pcsh.org/~pctao/wordpress/index.php?p=12
 [2]: http://lists.freebsd.org/pipermail/freebsd-current/2004-October/039086.html

 *[/etc/libmap.conf]: man libmap.conf