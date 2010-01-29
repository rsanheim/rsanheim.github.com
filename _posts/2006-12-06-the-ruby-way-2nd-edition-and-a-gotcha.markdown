--- 
wordpress_id: 291
layout: post
title: The Ruby Way, 2nd Edition, and a gotcha
wordpress_url: http://www.robsanheim.com/?p=291
---
<a href="http://www.amazon.com/gp/product/0672328844?ie=UTF8&tag=panasonicyout-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0672328844"><img class="right" border="0" src="http://images.amazon.com/images/P/0672328844.01._AA_SCMZZZZZZZ_V34026226_.jpg"/></a><img src="http://www.assoc-amazon.com/e/ir?t=panasonicyout-20&l=as2&o=1&a=0672328844" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" />
This <a href="http://www.linuxjournal.com/node/1000140">review</a> of the <a href="http://www.amazon.com/gp/product/0672328844?ie=UTF8&tag=panasonicyout-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0672328844">The Ruby Way, Second Edition</a><img src="http://www.assoc-amazon.com/e/ir?t=panasonicyout-20&l=as2&o=1&a=0672328844" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" /> mentions one of Ruby's fun little corners.  To illustrate, what is the value of "doop" after this code?
<pre><code>
x = true
y = false
doop = y or x
</code></pre>
The correct answer is "false" because the "and" and "or" operators in Ruby have lower precedence then the assignment operator.  There is a <a href="http://www.linuxjournal.com/node/1000140#comment-198876">detailed explanation</a> in the comments of the review, but the gist of it is this: use the standard boolean operators (&& and ||) for normal, everyday cases.  Use their english counterparts when only when you really want their very low precedence to make your code cleaner.

As an aside, I'm only a few chapters in to my copy of the Ruby Way and I can tell already its going to up there with the PickAxe and Ruby for Rails, particularily for more advanced programmers.  Fulton covers all sorts of fun little gotchas and corner cases found in Ruby, things that you maybe ran into once and couldn't figure out or things that maybe you'll never run into.  So far I would say its a little bit like the classic <a href="http://www.amazon.com/gp/product/0201310058?ie=UTF8&tag=panasonicyout-20&linkCode=as2&camp=1789&creative=9325&creativeASIN=0201310058">Effective Java </a><img src="http://www.assoc-amazon.com/e/ir?t=panasonicyout-20&l=as2&o=1&a=0201310058" width="1" height="1" border="0" alt="" style="border:none !important; margin:0px !important;" /> in how it takes a task based approach to showing the Ruby way to do things and the tradeoffs involved with different approaches.

Speaking of Effective Java, whatever happened to the talk of a second edition of it?
