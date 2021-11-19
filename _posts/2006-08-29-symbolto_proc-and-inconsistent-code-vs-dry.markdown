--- 
wordpress_id: 261
layout: post
title: Symbol#to_proc and inconsistent code vs DRY
wordpress_url: https://www.robsanheim.com/?p=261
---
Jeremy <a href="https://www.jvoorhis.org/articles/2006/08/29/on-writing-well-exposition-or-code">recently wrote</a> some good tips on cutting back on your code base, but his last tip is one I'm not sure about.  It recommends using the <a href="https://blogs.pragprog.com/cgi-bin/pragdave.cgi/Tech/Ruby/ToProc.rdoc">Symbol#to_proc</a>  (<a href="https://redhanded.hobix.com/cult/symbolTo_procExonerated.html">in ActiveSupport, coming in ruby 1.9</a>) shortcut for simple enumerable calls.  Like many rubyists, I appreciate the elegance and DRYness of to_proc, as you can go from this:
[ruby]pugs.map { |pug| pug.bathe! }[/ruby]
to this:
[ruby]pugs.map &:bathe![/ruby]
I don't like repeated the "pug" in the that first construct, but it is more obvious to newbies.  But I don't think thats a huge issue - explaining to_proc isn't hard.

My main issue is you can only use to_proc for the simplest cases, so your collection methods end up looking inconsistent.  Consider the following:
[ruby]pugs.select { |pug| !pug.clean? } # or
pugs.map { |pug| pug.feed(diet_dog_food)[/ruby]
Since these calls aren't a simple property call, but involve operating on a property or passing in a parameter, you can't use to_proc.  It hurts my eyes to see a model with eight collection methods, three of which using to_proc since they can, and the other five using traditional syntax.  I love beautiful code, and when things get inconsistent they get ugly.   Right now I'm still using both methods where appropriate, so I'm still undecided...

Further reading: <a href="https://www.pinupgeek.com/articles/2006/06/16/symbol-to_proc-thy-fearful-symmetry">possible changes</a> to the implementation of to_proc for ruby 1.9, read only when you have some uniterrupted time to digest.
