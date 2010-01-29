--- 
wordpress_id: 262
layout: post
title: Deprecation in Rails, and What You Can Do About It
wordpress_url: http://www.robsanheim.com/?p=262
---
Now that the sound and fury over <a href="http://glu.ttono.us/articles/2006/08/30/guide-things-you-shouldnt-be-doing-in-rails">Kevin's post</a> on the old and busted in Rails is calming down, we do have some nice constructive resources.  One is Geoffrey's <a href="http://nubyonrails.topfunky.com/articles/2006/08/31/deprecated-plugin-find-old-rails-code">Deprecated Plugin</a> which greps your code for things like @params or render_partial.  Very nice, and he's going to rewrite it so its not dependant on grep, so those poor win32 people can use it.  Those guys probably don't care about deprecated stuff anyways, as they are too busy lusting after macbooks.  Thats a little "geek humor" for you there...

A <a href="http://wiki.rubyonrails.com/rails/pages/Deprecated+Patterns/">Deprecated Patterns</a> page on the wiki got some love, and <a href="http://jim.eponym.com/blog/_archives/2006/8/31/2283270.html">Jimmy</a> took some steps to flesh it out and I added a few things here and there.  So go and add anything you think is missing, and keep that url handy to pass along on rails-talk.  My call for http://deprecated.rubyonrails.org went unheeded, but the wiki will be good enough.  Until it gets crushed with spam again, that is.  Maybe <a href="http://wikis.onestepback.org/Ruse/page/show/FrequentlyAskedQuestions">Ruse</a> should take the place of i2 for the rails wiki?

I've also heard talk of the ajax helpers being removed from core, but haven't seen it from the trac feed yet.  Is that happening in time for 1.2?
