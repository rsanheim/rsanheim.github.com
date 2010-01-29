--- 
wordpress_id: 114
layout: post
title: Multiple feeds suck - switching to Feedburner and one feed
wordpress_url: http://www.robsanheim.com/?p=114
---
<img class="right" src='/wp-content/rsssucks.png' alt='rss sucks' />
As has been written <a href="http://www.shtuff.us/weblog/109/feed-subscription-usability">about</a> <a href="http://www.veen.com/jeff/archives/000733.html">many</a> <a href="http://www.mezzoblue.com/archives/2003/11/05/plugging_the/">times</a> <a href="http://scobleizer.wordpress.com/2005/10/30/rss-usability-sucks/">before</a>, having a bunch of different feeds with different names and formats is horrible from a usability standpoint and just dumb to begin with.  Even I find it confusing when I try to add a blog to <a href="http://www.bloglines.com">Bloglines</a> and I'm confronted with five different options, and I'm a big geek.

So I setup a <a href="http://www.feedburner.com">Feedburner</a> account, and with the help of a <a href="http://orderedlist.com/articles/wordpress-feedburner-plugin/">nice Wordpress plugin</a> all the old feeds should redirect to that.  Then a quick edit to the header template reduced the auto-discovery feeds to just the Feedburner one.  Feedburner's <a href="http://www.burningdoor.com/feedburner/archives/000520.html">SmartFeed</a> can take care of the multiple formats, and now there is just one link to worry about for subscribing.

(side note: Bloglines uses its own database of known feeds for a site, which is why if you try to add my site, for example, you still get five or six feeds.  Apparently they will die over time as the redirects work.)
