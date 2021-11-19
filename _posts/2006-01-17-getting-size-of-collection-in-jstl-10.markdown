--- 
wordpress_id: 166
layout: post
title: Getting size of collection in JSTL 1.0
wordpress_url: https://www.robsanheim.com/?p=166
---
Assuming <strong><a href="https://jakarta.apache.org/taglibs/doc/standard-1.0-doc/intro.html">JSTL 1.0</a></strong>, this doesn't work:

<code>&lt;c:out value="${myMap.size}" /&gt;</code>

and neither does this

<code>&lt;c:set var="mapSize" value="${myMap.size}" /&gt;<br />
&lt;c: out value="${mapSize}" /&gt;</code>

I'm assuming JSTL wants to find something called getSize()...
So is this the only way to do it?

<code>&lt;%=((java.util.Map) pageContext.findAttribute("myMap")).size() %&gt;</code>

(meta note: if I actually get all the HTML escape codes right for this, I will be amazed)
