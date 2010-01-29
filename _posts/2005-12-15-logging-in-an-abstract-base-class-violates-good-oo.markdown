--- 
wordpress_id: 118
layout: post
title: Logging in an abstract base class - violates good OO?
wordpress_url: http://www.robsanheim.com/?p=118
---
Scenario: you are starting a project and have created three classes that all do their own standard log setup, creating private static logs or whatever.  Does creating an abstract base type with standard logging functionality violate <a href="http://xp.c2.com/YouArentGonnaNeedIt.html">YAGNI</a>, the <a href="http://c2.com/cgi/wiki?SingleResponsibilityPrinciple">single responsiblity principle</a>, or something else?  

A couple immediate problems I can see with the base type are too much coupling to the logging system for your objects, and having the bloated interface for objects that do not need the logging.  Also, you'll end up repeating yourself anyways when you have to extend base classes from frameworks.

I suppose this is really a case where I just want something like <a href="http://www.rubycentral.com/book/tut_modules.html">Ruby's mixins</a>.
