--- 
wordpress_id: 378
layout: post
title: log_buddy Released - your helpful little dev buddy
wordpress_url: https://robsanheim.com/2008/03/28/log_buddy-released-your-helpful-little-dev-buddy/
---
<a href="https://opensource.thinkrelevance.com/wiki/log_buddy">LogBuddy</a> is your friendly little log buddy at your side, helping you dev, debug, and test.  It plays well with Rails and plain old Ruby projects.  To use it, sudo gem install log_buddy, then require 'log_buddy' and call LogBuddy.init.  It will add two methods to object instance and class level: "d" and "logger".  You probably only want to use it in non-production environments.

<ul><li>The "logger" method is just a typical logger - it will use the Rails logger if its available.  </li>
<li>The "d" method is a special helper that will output the code in the block and its result - note that you *must* use the bracket block form - do...end is not supported.</li></ul>Examples

```ruby
require 'lib/log_buddy'
LogBuddy.init

a = "foo"
@a = "my var"
@@bar = "class var!"
def bark
 "woof!"
end

module Foo;
  def self.module_method
    "hi!!"
  end
end
  
d { a }                   # logs "a = 'foo'"
d { @a }                  # logs "@a = 'my var'"
d { @@bar }               # logs "@@bar = 'class var!'"
d { bark }                # logs "bark = woof!"
d { Foo::module_method }  # logs Foo::module_method = 'hi!!'
```

<h3>More Details</h3>

<ul>
<li>Log bugs/issues/suggestions here: <a href="https://opensource.thinkrelevance.com/wiki/log_buddy">https://opensource.thinkrelevance.com/wiki/log_buddy</a></li>
<li>Source: <a href="https://github.com/relevance/logbuddy/tree/master">https://github.com/relevance/logbuddy/tree/master</a></li>
<li>git clone git://github.com/relevance/logbuddy.git</li>
<li>rdocs: <a href="https://thinkrelevance.rubyforge.org/log_buddy/">https://thinkrelevance.rubyforge.org/log_buddy/</a></li>
</ul>

