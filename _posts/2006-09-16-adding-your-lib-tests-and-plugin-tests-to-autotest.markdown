--- 
wordpress_id: 265
layout: post
title: Adding your Lib Tests and Plugin Tests to Autotest
wordpress_url: http://www.robsanheim.com/?p=265
---
My work lately has involved managing a lot of common code across three different Rails projects, some of it managed by svn:externals in /lib and some in plugins.  So since I've been using ZenTest's <a href="http://rubyforge.org/projects/zentest/">autotest</a> (which is very nice with the growl and redgreen plugins in 3.4), naturally I want the lib and vendor/plugin tests picked up as well.  Heres my solution, crude as always, added to the case statement in rails_autotest.rb - it assumes your tests follow the Rails pattern of "[implementation file]_test.rb":

[ruby].... 
    when %r%^lib(.*)_test\.rb$% then
      [filename]
    when %r%^vendor/plugins(.*)_test\.rb$% then
      [filename]
    .....[/ruby]

The "right" way to do this would be to open up RailsAutotest in the dot autotest file, alias and chain tests_for_file to a new implementation that does the above.  But when its just 4 lines to add in, I'm not too worried about it - maybe the next version will have some easy method to append additional filename conditions for rails.

Note that this only picks up the tests when you actually change something in the test file - the tests aren't loaded at startup.  Once you change a test, it gets included in future runs until you exit autotest.  This is good enough for me, but if you add the other regex's needed to catch the reverse mapping (ie foo_bar_plugin.rb maps to foo_bar_plugin_test.rb), please do comment or link back with them.
