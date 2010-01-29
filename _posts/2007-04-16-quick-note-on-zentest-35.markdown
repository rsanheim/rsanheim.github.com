--- 
wordpress_id: 311
layout: post
title: Quick Note on zentest 3.5
wordpress_url: http://www.robsanheim.com/?p=311
---
Ryan <a href="http://blog.zenspider.com/archives/2007/04/zentest_version_350_has_been_released.html">released zentest 3.5</a> last week, and for some reason a normal 'sudo gem update' wasn't picking it up.  Searching remote gems for 'zentest' reveals why:

<pre><code>*** REMOTE GEMS ***
ZenTest (3.4.3, 3.4.2, 3.4.1, 3.4.0, 3.3.0, 3.2.0, 3.1.0, 3.0.0)
    ZenTest provides 4 different tools and 1 library: zentest,
    unit_diff, autotest, multiruby, and Test::Rails.

zentest (3.5.0)
    ZenTest provides 4 different tools and 1 library: zentest,
    unit_diff, autotest, multiruby, and Test::Rails.
</code></pre>

So the latest version is actually seen as a brand new gem, or at least my system (mac osx) sees it as such.  Gem update would not grab 3.5, since my old version of it was installed as "ZenTest".  If you have this problem, just do 'sudo gem install zentest' to grab the latest and then:

<pre><code>[Cassiopeia:/sa/saplatform] $ sudo gem uninstall ZenTest -v 3.4.3

You have requested to uninstall the gem:
        ZenTest-3.4.3
memcache-client-1.3.0 depends on [ZenTest (>= 3.4.2)]
rc-rest-2.2.1 depends on [ZenTest (>= 3.4.2)]
cached_model-1.3.1 depends on [ZenTest (>= 3.4.1)]
If you remove this gems, one or more dependencies will not be met.
</code></pre>
If you do get that warning, it should be safe to ignore since 3.5 will be loaded and used fine.  I guess rubygems just doesn't know that ZenTest == zentest.

<b>Update:</b> Oops, it is a problem:
<pre><code>
irb(main):002:0> require 'memcache'
Gem::LoadError: Could not find RubyGem ZenTest (>= 3.4.2)

        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:301:in `report_activate_error'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:238:in `activate'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:264:in `activate'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems.rb:263:in `activate'
        from /usr/local/lib/ruby/site_ruby/1.8/rubygems/custom_require.rb:31:in `require'
        from (irb):2
</code></pre>

I've opened a <a href="http://rubyforge.org/tracker/index.php?func=detail&aid=10144&group_id=419&atid=1678">bug.</a>  Work around it now by keeping the old version installed, or install it by specifying the version: "sudo gem install -v 3.4.3 ZenTest".
