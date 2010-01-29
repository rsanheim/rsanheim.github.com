--- 
wordpress_id: 184
layout: post
title: How to write good error messages
wordpress_url: http://www.robsanheim.com/?p=184
---
An anonymous <a href="http://www.oftedal.no/~erlend/">javaBlogger</a> <a href="http://www.oftedal.no/~erlend/?blogid=9">posted</a> about crummy error messages in many common frameworks today.   His complaint was with messages like this:

<ul><li>Wrong string format</li><li>Cannot open file</li><li>Unable to contact server</li></ul>

And proprosed changing them to include the offending input:

<ul><li>Wrong string format in state code: "WI_1234"</li>
<li>Cannot open file: my.settings</li>
<li>Unable to contact server: your.mom.com</li></ul>

I would say go even further.  Explain exactly why the input failed and what input is expected.  For example:

<ul><li>Wrong string format in state code: "WI_1234" -- state codes must be in the format of: "AB:1234" and are case sensitive.</li>
<li>Cannot open file: my.settings -- the file was not found, make sure its in /path/to/resources/.</li>
<li>Unable to contact server: your.mom.com - returned error code 500 -- ensure that the server can respond to HTTP requests on port 8080</li></ul>

Put your self in the role of the user who is just starting out with your framework.  And by "user" it could be a programmer extending your framework, a teammate using your interface, or Joe User trying to use your GreaseMonkey script.  Imagine what would be helpful for someone who knows absolutely nothing about the inner workings of your program, and what sort of information would be helpful when things go wrong.  Graham <a href="http://www.paulgraham.com/hp.html">wrote</a> "Empathy is probably the single most important difference between a good hacker and a great one."  So have some empathy, and spend a little more time on those error messages.
