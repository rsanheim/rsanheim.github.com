--- 
wordpress_id: 148
layout: post
title: Prototype and extending javascript's Object or Array
wordpress_url: https://www.robsanheim.com/?p=148
---
<img class="right" src="https://prototype.conio.net/images/prototype.png"/>James McParlane wrote a entry detailing <a href="https://blog.metawrap.com/blog/WhyIDontUseThePrototypejsJavaScriptLibrary.aspx">why he won't use the Prototype library,</a> as extending Object or Array's builtin prototype is <a href="https://erik.eae.net/archives/2005/06/06/22.13.54/">bad.</a>  

However, Sam heard the complaints about how Prototype 1.3.1 was breaking existing code and other libraries, and the newer relases all use <a href="https://dev.conio.net/repos/prototype/src/base.js">Object.extend() </a>for safe extensions and do not change Array's prototype.  Note that the prototype <a href="https://prototype.conio.net/">home page</a> still only lists the old 1.3.1 version, which may be confusing some people.  So either <a href="https://dev.conio.net/repos/prototype/dist/prototype.js">download just the .js file</a>, or <a href="https://script.aculo.us/downloads">grab the latest Scriptaculous</a> which has the 1.4 final also, and use the <a href="https://developer.mozilla.org/en/docs/Core_JavaScript_1.5_Guide:Object_Manipulation_Statements">for...in</a> without fear.
