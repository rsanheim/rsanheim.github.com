--- 
wordpress_id: 245
layout: post
title: "Evil magic: Getting the name of a method within the method in Ruby (or Java?)"
wordpress_url: https://www.robsanheim.com/?p=245
---
During my dark days of java, I often wanted to be able to reflectively get the name of the method called inside the method in order to log things, inspect things, etc.  It was always impossible, at least as far as I knew back then - though in light of new knowledge, I wonder if you couldn't throw an exception, then catch it and inspect the stack trace? 

Anyways, <a href="https://article.gmane.org/gmane.comp.lang.ruby.general/158740/match=method">saw on ruby-lang</a> this little trick to do it in ruby:

[ruby]def method_called
 caller[0].match(/`([^']+)/).captures[0]
end

def test_me
 p method_called
end

test_me
#=> "test_me"
[/ruby]

Its a bit hacky and evil, and I'm sure its not fast, but it works.
