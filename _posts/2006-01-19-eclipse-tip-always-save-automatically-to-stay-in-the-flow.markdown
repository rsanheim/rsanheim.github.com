--- 
wordpress_id: 158
layout: post
title: "Eclipse tip: always save automatically to stay in the flow"
wordpress_url: http://www.robsanheim.com/?p=158
---
I almost never want to be asked if I want to save an editor window in Eclipse.  With the safeguards of version control and local history, there is never a save that cannot be reverted easily.  When I'm really in the flow, I want the cycle to be seamless between edit test case, ctrl-f11 (run test), modify code under test, ctrl-f11 (run test), etc....  Having a window popup after each little code modification is very annoying and slows you down.

If you check the following preferences, you should almost never be asked for confirmation for save.  The only time I still get asked is if I close an editor window that hasn't been saved, as I haven't found a auto save option for it yet.  So, go check these preferences in Eclipse:
<!--more-->

<img src='/wp-content/save_before_build.png' alt='eclipse screenshot - save before build' />

Always save before building (Eclipse will auto build before launching and running tests).

<img src='/wp-content/save_before_launch.png' alt='Eclipse screen shot - save before launch' />

Always save before launch (ie before running Junit tests or your test server).

<img src='/wp-content/save_before_refactoring.png' alt='Eclipse screenshot - save before refactoring' />

Finally, auto save before doing any refactoring, so things are in a consistent state.
