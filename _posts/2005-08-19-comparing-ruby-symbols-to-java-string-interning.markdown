--- 
wordpress_id: 56
layout: post
title: Comparing Ruby Symbols to Java String interning
excerpt: Ruby Symbols are kinda like interned Strings in Java, only different
wordpress_url: https://www.robsanheim.com/?p=56
---
If I'm reading the <a href="https://glu.ttono.us/articles/2005/08/19/understanding-ruby-symbols">Kev's article</a> on Ruby symbols correctly, they are kinda the same as Java <a href="https://mindprod.com/jgloss/interned.html">interned Strings</a>...except with some more power.  A Symbol also is its own type, which would also be somewhat different from Java Strings.  It kinda helps explain all the weird keys (to my eyes) used in Rails, so you aren't recreating the "link" key 500 times in memory.   <a href="https://groups-beta.google.com/group/comp.lang.ruby/browse_thread/thread/aaffddc5b3c0dc79/">This post</a> in Ruby-Talk (<a href="https://rubygarden.org/ruby/ruby?RubyNews/2005-01-31">via RubyNews</a>) also provides a nice explanation, which I will quote for your too-lazy-to-click convience:

<em>Symbols are immutable strings. Every occurence of the same symbol correspondes to the same single object, while every occurence of the same string is a different object (with the same value). Thus symbols are a bit faster and cheaper to use in things like case statements, hash keys etc.

It's also usually a bit nicer to read in the code, as it signifies that what you're looking it at is a unique identifier, rather than something that can have a dynamic content.</em> - (thanks Assaph Mehr)
