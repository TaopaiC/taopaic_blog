---
title: make buildkernel -DALWAYS_CHECK_MAKE
author: TaopaiC
layout: post
permalink: /2004/10/13/19
wheredidtheycomefrom:
  - 's:28:"a:2:{i:0;i:20;i:1;s:2:"16";}";'
categories:
  - FreeBSD
---
從 5.2.1-RELEASE 要弄到 5-current 的時候, 發生 make error, +for 不認識.  
記一下 -DALWAYS\_CHECK\_MAKE  
<!--more-->

<blockquote title="To build a kernel" cite="/usr/src/UPDATING">
  <p>
    /usr/src/UPDATING 這麼說的
  </p>
  
  <p>
    To build a kernel<br /> &#8212;&#8212;&#8212;&#8212;&#8212;&#8211;<br /> If you are updating from a prior version of FreeBSD (even one just<br /> a few days old), you should follow this procedure. With a<br /> /usr/obj tree with a fresh buildworld,<br /> make -DALWAYS_CHECK_MAKE buildkernel KERNCONF=YOUR_KERNEL_HERE<br /> make -DALWAYS_CHECK_MAKE installkernel KERNCONF=YOUR_KERNEL_HERE
  </p>
</blockquote>

References:

*   [Upgrade to 5.3-BETA1: make installkernel &#8211; Stop in /usr/src/sys/modules][1] 
    http://lists.freebsd.org/pipermail/freebsd-current/2004-August/035255.html
    
    Christian Hiris 4711 at chello.at  
    Tue Aug 24 07:41:23 PDT 2004</li> </ul>

 [1]: http://lists.freebsd.org/pipermail/freebsd-current/2004-August/035255.html