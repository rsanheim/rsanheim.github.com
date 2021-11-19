--- 
wordpress_id: 365
layout: post
title: Beware the default nginx config - old IE6 hates gzip
wordpress_url: https://robsanheim.com/2008/02/07/beware-the-default-nginx-config-old-ie6-hates-gzip/
---
<p>I had some issues with an application deployed to <a href="https://engineyard.com/" title="Engine Yard">EngineYard</a> recently, using their standard nginx config with a few mongrels behind it.  The issue was <em>only</em> happening with IE6, and only happening intermittently.  And of course, I could not reproduce it locally.  After some fun-filled research and gotomeeting&#8217;s with folks who saw the issue, it turned out it was only happening in pre service pack 2 versions of IE6.</p>

<p>I was aware that there were <a href="https://support.microsoft.com/default.aspx?scid=kb;[LN];Q312496" title="Internet Explorer May Lose the First 2,048 Bytes of Data That Are Sent Back from a Web Server That Uses HTTP Compression">known</a> <a href="https://www.microsoft.com/Downloads/details.aspx?FamilyID=5a05e071-29ff-4dd3-836a-879ffdb56e27&amp;displaylang=en" title="Download details: IE6 Update: Data is Truncated When You Download a gzip-Encoded Excel File in Internet Explorer">issues</a> with older versions of IE and gzipping, so I took a look at the nginx config.  This was a config that EngineYard installed standard, out of the box.  The gzip section looked like this:</p>

<pre><code>gzip            on;
gzip_http_version 1.0;
gzip_comp_level 2;
gzip_proxied any;
gzip_buffers 16 8k;
gzip_types      text/plain text/html text/css .... # etc
</code></pre>

<p>The issue here is that you are serving gzipp&#8217;ed content to every browser that claims they can take it, even crappy browsers that totally suck and will bark every 5th request on some gzipp&#8217;ed css or js.</p>

<p>Beware: these settings are what you find commonly from <a href="https://www.slashdotdash.net/articles/2007/07/31/rails-performance-tip-using-yslow" title="Rails performance tip - using YSlow">different</a> <a href="https://topfunky.net/svn/shovel/nginx/conf/nginx.conf" title="">Rails</a> <a href="https://docs.planetargon.com/Nginx_Configuration/" title="Nginx Configuration">sites</a> with ngninx config templates.</p>

<p>The solution is simple - add the following line to your nginx config:</p>

<pre><code>gzip_disable "MSIE [1-6]\.";
</code></pre>

<p>Yes, this will exclude versions of IE6 that <em>can</em> safely take gzip, but I didn&#8217;t have the time or inclination to find the user agent regex fu to only exclude IE6 SP1 and older.  Comments appreciated if you refine it to only exclude IE6 SP1 and lower.</p>

<p><strong>Update</strong> Thanks to Jauder in the comments for the better regex to only get the versions we really want:</p>

<pre><code>gzip_disable "MSIE [1-6]\.(?!.*SV1)";</code>
</pre>
