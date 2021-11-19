--- 
wordpress_id: 208
layout: post
title: Searching for the perfect in memory database
wordpress_url: https://www.robsanheim.com/?p=208
---
I've been using <a href="https://hsqldb.org/">HSQLDB</a> for my <a href="https://www.martinfowler.com/bliki/InMemoryDatabase.html">in memory database</a> testing, but I think its time to find something else.  Things have been getting pretty painful lately and I'm wondering what kind of experience others have with the alternatives.  My criteria are:
<ul><li>fast</li>
	<li>easy to embed in a Java test suite - so basically just drop in the database, a property file and the jdbc driver and go</li>

	<li>excellant support for the sql standard - including all the outer joins, some core set of conversion functions, etc</li>

	<li>support full outer join</li>
	<li>did I mention fast?</li>
	</ul>

My latest query is doing <a href="https://en.wikipedia.org/wiki/Outer_join#Full_outer_join">full outer joins</a> and HSQLDB <a href="https://sourceforge.net/forum/message.php?msg_id=3521026">doesn't</a> like it.  Just checked out <a href="https://www.sqlite.org/">Sqllite</a>, but it has the same problem as HSQLDB - left outer joins supported, but nothing else.  

<a href="https://db.apache.org/derby/">Derby</a> looks like an option, as they <a href="https://wiki.apache.org/db-derby/SQLvsDerbyFeatures">claim</a> support for right outers and left outers, but no full outer.  I may take a look at Firebird next, but I can't find much on doing things embedded in an app without too much pain.
