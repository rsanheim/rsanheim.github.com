--- 
wordpress_id: 366
layout: post
title: "[ANN] brain_buster 0.8.0 released"
wordpress_url: http://robsanheim.com/2008/02/12/ann-brain_buster-080-released/
---
I'm happy to release version 0.8.0 of <a href="http://opensource.thinkrelevance.com/wiki/BrainBuster" title="BrainBuster - Relevance Open Source - Trac">BrainBuster</a>.  

This is a long overdue release.  I've removed all deprecated code, updated for Rails 2.0, improved specs considerably, and cleaned up the api and views.

Because of the way the filter chain is handled in Rails 2.0, you will now have to handle a captcha failure explicitly.  Right now thats just done by overriding a method in your controller.  See the <a href="http://opensource.thinkrelevance.com/browser/brain_buster/trunk/README">README</a> for more info.

I hope to post a quick tutorial for getting up and running with BrainBuster over the next few days, so please <a href="http://robsanheim.com/feed">watch for that</a> if you want to learn how to add an accessible, image free captcha to your app.

BrainBuster has now been moved to <a href="http://github.com/rsanheim/brain_buster/tree" title="rsanheim's brain_buster at master &mdash; GitHub">github for the dev scm</a>, and to the <a href="http://opensource.thinkrelevance.com/wiki/BrainBuster" title="BrainBuster - Relevance Open Source - Trac">Relevance Trac</a> for tickets and bugs.

The mailing list is still at <a href="http://groups.google.com/group/brainbuster-discuss" title="BrainBuster Discussion | Google Groups">google groups</a>.
