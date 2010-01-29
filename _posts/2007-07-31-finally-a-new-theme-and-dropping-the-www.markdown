--- 
wordpress_id: 332
layout: post
title: Finally, a new theme and dropping the www
wordpress_url: http://robsanheim.com/2007/07/31/finally-a-new-theme-and-dropping-the-www/
---
Finally, some long overdue updates here.

The old theme here was way beyond tired - I'm now using Derek's <a href="http://powazek.com/posts/516">wonderfully clean theme.</a>  I think I broke the feed for a little bit there, but it should be back up and properly redirecting to feed burner.

I also got rid of the www, so <a title="recursion!!" href="http://robsanheim.com">robsanheim.com</a> is officially <a href="http://no-www.org/">no-www</a> compliant now.  'www' is so '97.  The correct redirect code to drop into your .conf file follows. I noticed quite a few of the samples out there would end up with the double trailing slash problem when accessing the root url:

<code><pre>RewriteEngine On
RewriteCond %{HTTP_HOST} ^www\.robsanheim\.com/?$ [NC]
RewriteRule ^(.*)$ http://robsanheim.com$1 [R=301,L]
</pre></code>

I really do plan on writing about software here again very soon.  

<strong>also: </strong>I've started a tumblelog <a href="http://303.tumblr.com/">over here,</a> and I'm so late to the party that I don't even know if they are called "tumblelogs" anymore.  

<strong>Also:</strong> (not me):
<img src="http://www.patandfran.com/frontPagePics/cima_athf.jpg" />

