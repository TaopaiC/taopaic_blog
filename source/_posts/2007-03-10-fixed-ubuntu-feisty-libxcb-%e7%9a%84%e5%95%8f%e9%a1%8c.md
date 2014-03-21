---
title: '[fixed] ubuntu feisty &#038; libxcb 的問題'
author: TaopaiC
layout: post
permalink: /2007/03/10/179
tags:
  - 
wheredidtheycomefrom:
  - 's:30:"a:2:{i:0;i:180;i:1;s:3:"177";}";'
categories:
  - Linux
---
之前提到 [libxcb 的問題][1], ubuntu feisty 終於有新的更新, 不用自己動手了. <!--more-->

  
[libxcb 1.0-1.1ubuntu1][2] 暫時避免這個問題. 預設是關掉檢查lock的機制, 如果要啟用的話, 只要設定LIBXCB\_NO\_SLOPPY_LOCK為任何值即可.

[libxcb 1.0-1.1ubuntu2][3] 則是修正前述patch在building時沒被使用的問題 ([Bug #90757][4]).

附上libxcb的ChangeLog

> libxcb (1.0-1.1ubuntu2) feisty; urgency=low
> 
> * debian/patches/: Create & place 100\_allow\_sloppy_lock.diff in quilt&#8217;s series index. Closes LP: #90757
> 
> &#8211; Daniel T Chen <crimsun> Thu, 8 Mar 2007 20:47:14 -0500  
> </crimsun>

> libxcb (1.0-1.1ubuntu1) feisty; urgency=low
> 
> [ Timo Aaltonen ]  
> * debian/patches:  
> - 100\_allow\_sloppy\_lock.diff from Novell, workaround to the various &#8216;Assertion \`c->xlib.lock&#8217; failed"&#8216; -bugs by setting an environment variable LIBXCB\_ALLOW\_SLOPPY\_LOCK to any value and the check will simply be ignored.  
> * debian/{control,rules}:  
> - add quilt to Build-deps, and patchsys-quilt.mk to rules.  
> - change Maintainer address.
> 
> [ Martin Pitt ]  
> * 100\_allow\_sloppy\_lock.diff: Reverse the patch logic for Feisty: Use sloppy locking by default for now, because we won&#8217;t have time to discover and fix all broken apps. Setting LIBXCB\_NO\_SLOPPY\_LOCK will enable the strict behaviour. This should be dropped right at the opening of Feisty+1.
> 
> &#8211; Timo Aaltonen <tepsipakki> Wed, 7 Mar 2007 08:27:01 +0100</tepsipakki>

 [1]: http://pctao.org/2007/03/05/177/
 [2]: https://launchpad.net/ubuntu/feisty/+source/libxcb/1.0-1.1ubuntu1
 [3]: https://launchpad.net/ubuntu/feisty/+source/libxcb/1.0-1.1ubuntu2
 [4]: https://launchpad.net/ubuntu/+source/libxcb/+bug/90757