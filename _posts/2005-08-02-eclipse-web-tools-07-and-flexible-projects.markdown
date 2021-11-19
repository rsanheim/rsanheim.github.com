--- 
wordpress_id: 37
layout: post
title: Eclipse Web Tools 0.7 and flexible projects
wordpress_url: https://www.robsanheim.com/?p=37
---
Guillermo <a href="https://javageek.org/2005/08/02/wpt_0_7_out_hold_your_horses.html">blogged </a> about his experience with <a href="https://download.eclipse.org/webtools/downloads/drops/R-0.7-200507290654/">WTP 0.7</a> and the lack of project refactorings and ability to change default JavaSource & WebContent folders.  This has been an issue that's bothered me for awhile.  I've been amazed at the attention given to allowing "flexible projects" with WTP - meaning mulitple modules within one project - while the seemingly simple task of having user defined paths has been ignored.

Anyways, the requests are out there, so go vote for them and add your two cents:
<a href="https://bugs.eclipse.org/bugs/show_bug.cgi?id=102981">Bug 102981</a> - configurable JavaSource and WebContent
<a href="https://bugs.eclipse.org/bugs/show_bug.cgi?id=102527">Bug 10257</a> - ability to refactor projects (ie change Java project to Web project), which is a bigger issue then just WTP

Note that even if you choose to go with <a href="https://www.myeclipseide.com/">MyEclipse,</a> its a good idea to still follow WTP as MyEclipse is going to be built on the latest WTP eventually.
