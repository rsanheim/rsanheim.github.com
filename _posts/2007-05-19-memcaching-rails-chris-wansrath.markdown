--- 
wordpress_id: 323
layout: post
title: RailsConf 2007 - Memcaching Rails - Chris Wansrath
wordpress_url: https://www.robsanheim.com/?p=323
---
	<ul>
		<li>Chris Wanstrath helped scaling gamespot</li>
		<li>had to turn off gzipping to avoid burning the cpus</li>
		<li>3000 req/seconds</li>
		<li>50M pages in the day, no downtime</li>
		<li>Chris is a sloppy programmer (jk)</li>
	</ul>

	<ul>
		<li>a distributed hash with no each or keys &#8211; just get and set</li>
		<li>written in c &#8211; fast</li>
	</ul>

	<ul>
		<li>at first &#8211; you dont need <a href="https://www.danga.com/memcached/">memcached</a> &#8211; YAGNI</li>
		<li>unless you really do need it - you have a millions of views, you have a huge DB, you have really ugly sql</li>
	</ul>

	<ul>
		<li>the standard pattern&#8212;try the cache first, if its not there, grab it from the DB and set it in the cache</li>
		<li>use memcached-client, not ruby-memcache</li>
		<li><a href="https://require.errtheblog.com/plugins/browser/cache_fu">cache-fu</a> = acts_as-cache 2.0</li>
		<li>don&#8217;t use DNS names for the servers &#8211; always use ip&#8217;s</li>
		<li>expire_cache &#8211; issues a delete to the cache</li>
		<li>get_cache &#8211; duh, grab from the cache</li>
		<li>so after_save :expire_cache</li>
	</ul>

	<ul>
		<li>you dont ever cache nil &#8211; since that screws ruby.  cache_fu will cache false behind the scenes</li>
		<li>get the DB down to 0.0% </li>
		<li>Model.cached(:finder)&#8212;wraps the idiom of caching a custom finder</li>
	</ul>

	<ul>
		<li>can do Model.get_cache(1,2,3) to do a get_multi call to memcached ( ie get many objects in parallel)</li>
		<li>can do a before_filter to force all cache misses when a url gets a magic query string </li>
		<li>but be careful &#8211; don&#8217;t crash your site</li>
		<li>use reset_cache!</li>
	</ul>

	<ul>
		<li>need :version to invalidate old version of AR models&#8212;otherwise you get screwed when you do a migration</li>
		<li>libketama &#8211; developed by lastfm guys so you can throw memcache servers in and out w/o invalidating all your keys</li>
		<li>the perl client already handles this under the covers, the ruby client doesn&#8217;t</li>
		<li>someone should implement libketama in ruby, to make big memcached installations safer</li>
	</ul>
