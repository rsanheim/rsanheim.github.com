--- 
wordpress_id: 77
layout: post
title: I hate when I rewrite API code
wordpress_url: https://www.robsanheim.com/2005/09/23/i-hate-when-i-rewrite-api-code/
---
Just spent five minutes writing code to iterate over a string and break out its lines nicely.  After a couple googles to check an API method, I see that <a href="https://java.sun.com/j2se/1.4.2/docs/api/">BreakIterator</a> has already done it for me in the java.text package.  The moral of the store is to always google on the JDK before writing something that feels like it should be in the api.  (Annoyance: why doesn't BreakIterator impelment Iterator?)

<b>Update: </b>Never mind, BreakIterator turned out to be horribly over complicated for what I needed.  I'm sticking with what I wrote in the first place.  Sometimes you should rewrite the wheel when its a very simple need - and the available wheel is for more complex.
