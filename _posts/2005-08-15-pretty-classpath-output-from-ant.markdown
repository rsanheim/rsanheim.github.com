--- 
wordpress_id: 51
layout: post
title: Pretty classpath output from Ant
wordpress_url: http://www.robsanheim.com/?p=51
---
<a href="http://peeps.dallas.focus-technologies.com/roller/comments/lhankins/Weblog/more_readable_classpaths_for_ant">Pretty classpath output from Ant:</a>

How to take this:
current.classpath=d:\work\proto\dist\foo-toolkit.jar;d:\work\proto\lib\hiber
nate-2.1.8\lib\dom4j-1.4.jar;d:\work\proto\lib\commons-discovery-0.2\commons-discov
ery.jar;d:\work\proto\lib\hibernate-2.1.8\hibernate2.jar;d:\work\proto\lib\hibernat
e-2.1.8\lib\c3p0-0.8.4.5.jar;d:\work\proto\lib\hibernate-2.1.8\lib\cglib-full-2.0.2
.jar;d:\work\proto\lib\hibernate-2.1.8\lib\ehcache-0.9.jar;d:\work\proto\lib\hibern
ate-2.1.8\lib\jta.jar;d:\work\proto\lib\hibernate-2.1.8\lib\odmg-3.0.jar;d:\work\pr...

to this:

<code>
[echo]   Classpath is :
[echo]
[echo]   d:\work\proto\dist\foo-toolkit.jar
[echo]   d:\work\proto\lib\hibernate-2.1.8\lib\dom4j-1.4.jar
[echo]   d:\work\proto\lib\commons-discovery-0.2\commons-discovery.jar
[echo]   d:\work\proto\lib\hibernate-2.1.8\hibernate2.jar
[echo]   d:\work\proto\lib\hibernate-2.1.8\lib\c3p0-0.8.4.5.jar
[echo]   d:\work\proto\lib\hibernate-2.1.8\lib\cglib-full-2.0.2.jar
[echo]   d:\work\proto\lib\hibernate-2.1.8\lib\ehcache-0.9.jar
[echo]   d:\work\proto\lib\hibernate-2.1.8\lib\jta.jar
[echo]   d:\work\proto\lib\hibernate-2.1.8\lib\odmg-3.0.jar
[echo]   d:\work\proto\lib\hibernate-2.1.8\lib\oscache-2.0.jar
[echo]   d:\work\proto\lib\hibernate-2.1.8\lib\swarmcache-1.0rc2.jar
[echo]   d:\work\proto\lib\oracle-10g\classes12-10g.jar</code>

Using "propertyregex" to replace semicolons with new lines.



