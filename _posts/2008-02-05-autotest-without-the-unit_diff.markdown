--- 
wordpress_id: 364
layout: post
title: autotest without the unit_diff
wordpress_url: http://robsanheim.com/2008/02/05/autotest-without-the-unit_diff/
---
<p>Ever since getting ZenTest 3.9.1, it seems unit-diff is always turned on.  That means your output in autotest is noiser, and I prefer the normal output from my spec or test framework.  Anyways, I'm not sure what changed since earlier versions of autotest (maybe the rails command used to override the command string?), but here is a <a href="http://pastie.caboo.se/147643" title="#147643 - Pastie">simple diff at pastie</a> to allow you to turn off unit-diff.  Also submitted to the <a href="http://rubyforge.org/tracker/index.php?func=detail&amp;aid=17788&amp;group_id=419&amp;atid=1680" title="RubyForge: Patch for zentest">rubyforge project</a>.</p>

<p>You need to apply the above patch to allow you to conditionally pipe to unit_diff, otherwise the below config tweak will break autotest.</p>

<p>Once you have hacked your autotest.rb with that patch, then you can open your .autotest (either in your home folder or in a specific project), and do the following:</p>

<p>[ruby]
Autotest.add_hook :initialize do |at|
  at.unit_diff = nil
end
[/ruby]</p>

<p>See <a href="http://blog.davidchelimsky.net/articles/2008/01/15/rspec-1-1-2-and-zentest-3-8-0" title="RSpec-1.1.2 and ZenTest-3.8.0">David's helpful post</a> for more on autotest configs and tweaking.</p>

