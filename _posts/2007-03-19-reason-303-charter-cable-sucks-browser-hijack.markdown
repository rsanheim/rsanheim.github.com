--- 
wordpress_id: 305
layout: post
title: "Reason #303 Charter Cable Sucks - Browser Hijack"
wordpress_url: https://www.robsanheim.com/?p=305
---
Lately when I've been entering a plain old search query in the address bar of any browser on my mac, I get a useless search page from Charter Cable (my provider) instead of the normal google results:

<a href="https://www.flickr.com/photos/robsanheim/426503950/" title="Photo Sharing"><img src="https://farm1.static.flickr.com/173/426503950_99169f17d5.jpg" width="500" height="375" alt="charter hijacks my browser" /></a>

Apparently <a href="https://www.thedailypage.com/forum/viewtopic.php?t=19857">Charter does a 302 redirect</a> for any hit that would normally go to the default search page.  They do provide an "opt out" option, which is ridiculous because I never opted in to let them do this in the first place:

<a href="https://www.flickr.com/photos/robsanheim/426503976/" title="Photo Sharing"><img src="https://farm1.static.flickr.com/167/426503976_c902ec7da0_m.jpg" width="216" height="240" alt="charter hijacks my browser" /></a>

So I have to set and save a cookie in all the browsers I use, or else Charter will provide their own ad-filled search results by default.  It seems this is at the DNS level, so either i have to set this cookie continuously (I clear cookies often), or find a different DNS server to use.  Thanks a lot, Charter, way to piss off a customer who has been with you for years.

update: this story <a href="https://slashdot.org/articles/07/02/15/0432259.shtml">even made Slashdot</a> a little while ago..I wonder why it just started happening to me in the past week or so?
