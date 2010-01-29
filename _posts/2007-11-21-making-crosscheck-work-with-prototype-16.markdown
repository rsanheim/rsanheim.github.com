--- 
wordpress_id: 347
layout: post
title: Making CrossCheck work with Prototype 1.6
wordpress_url: http://robsanheim.com/2007/11/21/making-crosscheck-work-with-prototype-16/
---
We are using <a href="http://www.thefrontside.net/crosscheck">Crosscheck</a> for javascript unit tests lately.  Crosscheck has fake DOM implementations for Firefox 1.0, 1.5 and IE6 (!!), so it runs headless and it runs fast.  This is a tool I've wanted for a long time, but writing a fake browser is no small task so there are still quite a few places where things fall down.

One issue we hit rather quickly were some breakages when using Prototype 1.6 in IE6 tests that had anything to do with event handling or used the <a href="http://www.prototypejs.org/api/document/observe">DOMContentLoaded</a> event.  Tests would blow out with errors similar to the following (only for IE6, they work fine in Firefox tests):

<pre><code>
test_should_check_real_box_when_checked: Cannot read property "eventName" from undefined
 at file:/../test/javascripts/./../../public/javascripts/prototype.js:3842
 at checkbox_test.js:49
test_should_display_error_with_invalid_statement: Cannot read property "eventName" from undefined
 at file:/../test/javascripts/./../../public/javascripts/prototype.js:3842
 at checkbox_test.js:74
</code></pre>

The code under test all worked 100% in the browser, so we knew it was something strange between prototype and crosscheck.

The pragmatic solution we came up with was to hack prototype just slightly to work around these things.  I'm guessing that the right (read: time consuming) fix would be to dig into crosscheck's IE6 implementation, and figure out what is going on there.

You can grab a <a href="http://pastie.caboo.se/120691">diff against prototype 1.6 final</a> if you hit these same issues and want to fix them.
