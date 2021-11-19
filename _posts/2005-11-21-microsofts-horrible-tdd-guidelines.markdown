--- 
wordpress_id: 119
layout: post
title: Microsoft's horrible TDD guidelines
excerpt: So-called "guidelines" for TDD from Microsoft using Visual Studio 2005
wordpress_url: https://www.robsanheim.com/?p=119
---
There has been much wailing and gnashing of teeth on various mailing lists over the MS article: <a href="https://msdn2.microsoft.com/en-us/library/ms182521.aspx">Guidelines for Test-Driven Development</a> that was recently posted.  

Microsoft gets a lot of things wrong:

* write a "complete list of tests for a particular feature area" first
* then write the production code before the tests
* use the wizards to create the tests
* in typical VS style, the tool and the wizards dictate everything
* no mention of refactoring
* no mention on doing things in very small steps
* where are the feedback loops?

What a mess.  There has been quite a response amongst the TDD community:
- Michael Feathers has a <a href="https://www.artima.com/weblogs/viewpost.jsp?thread=137207">good post</a> on this.  
- <a href="https://www.xprogramming.com/blog/Page.aspx?display=HotNeedleOfInquiry">Ron Jeffries' response</a>
- <a href="https://www.jamesshore.com/Blog/Microsoft-Gets-TDD-Completely-Wrong.html">James Shore</a>
- <a href="https://samgentile.com/blog/archive/2005/11/18/32103.aspx">Sam Gentile</a>, with plenty of other links to other responses

