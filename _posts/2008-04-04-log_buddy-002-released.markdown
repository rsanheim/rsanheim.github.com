--- 
wordpress_id: 381
layout: post
title: log_buddy 0.0.2 released
wordpress_url: https://robsanheim.com/2008/04/04/log_buddy-002-released/
---
<h3>Description</h3>
log_buddy is your friendly little log buddy at your side, helping you dev, debug, and test.

<h3>Synopsis</h3>

Call LogBuddy.init to use log_buddy.  It will add two methods to object instance and class level: "d" and "logger".  You can
use your own logger with Logbuddy by passing it into init's options hash:
    
```
LogBuddy.init :default_logger => Logger.new('my_log.log')
```
    
Now you have your logger available from any object, at the instance level and class level:

```ruby
obj = Object.new
obj.logger.debug("hi")
class MyClass; end
MyClass.logger.info("heya")
```

You also have a method called "d" (for "debug") on any object, which is used for quick debugging and logging of things while you are developing.  Its especially useful while using autotest.  When you call the "d" method with an inline block, it will log the name of the things
in the block and the result.  Examples:

<h3>Changes</h3>

0.0.2
* rdocs
* support for multiple statements in one "d" call separated by semicolons

<h3>Installation</h3>
sudo gem install log_buddy
<a href="https://thinkrelevance.rubyforge.org/log_buddy">full docs here</a>
