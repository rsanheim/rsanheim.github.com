--- 
wordpress_id: 84
layout: post
title: Prototype Insertion, IE 6, tr's, and "invalid target element for this operation..."
wordpress_url: https://www.robsanheim.com/?p=84
---
After much hardship I'm giving up on trying to use <a href="https://prototype.conio.net/">Prototype's</a> <a href="https://www.sergiopereira.com/articles/prototype.js.html#Abstract.Insertion">Insertion</a> function for inserting new rows after a specified target row.  Everything I try works in Firefox but blows out in IE 6, which is the "supported platform".   After some searching it seems IE has inconsistent support for the <a href="https://msdn.microsoft.com/workshop/author/dhtml/reference/methods/insertadjacenthtml.asp">insertAdjacentHTML</a> method, and apparently for elements like TR and TBODY IE will throw an exception if the method is called on those methods.  In the latest prerelease there is a fix for tbodys, but nothing for tr, and my knowledge of dom manipulation fell short when trying to hack that in.  If anyone can see how to add that to prototype.js, please let me know.  This seems like something that would be commonly done with Rails apps for dynamically adding rows to a table, so its curious that I couldn't find anything via Google...
