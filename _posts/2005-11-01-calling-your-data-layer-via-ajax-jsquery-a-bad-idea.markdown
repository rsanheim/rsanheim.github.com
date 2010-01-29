--- 
wordpress_id: 98
layout: post
title: calling your data layer via Ajax (jsquery) - a bad idea?
excerpt: thoughts on jsquery and calling JDBC/ORM directly via ajax
wordpress_url: http://www.robsanheim.com/?p=98
---
Saw on <a href="http://www.ajaxian.com">ajaxian</a> a <a href="http://www.ajaxian.com/archives/2005/11/jsquery_ajax_ja.html">blurb</a> about <a href="http://www.jsquery.com/java-jsquery/index.html">jsquery</a>.  It is basically a library to grab data directly from your server side JDBC/ORM layer and expose it to your pages as a javascript array that follows the ResultSet interface.

I'm not sure of the wisdom of doing something like this.  This directly couples your view layer code to your data layer code.  Even if you just want a "quick and dirty" solution and don't care too much about MVC, I would rather write my JDBC calls in a seperate data layer and test that independantly, and then remote the model objects via DWR.  If you really want to be dirty you could just return your dom structure or XML from your servlet and not worry about any "true" model objects.  But why deal with the result set interface on the javascript side?  If you go with jsquery, where do you clean or strip your data?  How do you reuse that JDBC/ORM call in other places without violating DRY?  Maybe I'm missing something here...enlighten me.
