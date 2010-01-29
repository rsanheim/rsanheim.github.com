--- 
wordpress_id: 342
layout: post
title: multi_rails has been released
wordpress_url: http://robsanheim.com/2007/10/23/multi_rails-has-been-released/
---
<a href="http://multi-rails.rubyforge.org/">MultiRails</a> allows easy testing against multiple versions of Rails for
your Rails specific gem or plugin.

Use MultiRails to hook in Rails 2.0 testing in your continuous integration.  Still working on Rails 2.0 support?  Use MultiRails to see where your test suite falls down against the 2.0 preview releases of Rails.

sudo gem install multi_rails...view the README or the <a href="http://multi-rails.rubyforge.org/">main rdoc page</a> for instructions

MultiRails was initially developed by members of Relevance while developing Streamlined against edge Rails.  To see how Streamlined uses MultiRails, go to <a href="http://trac.streamlinedframework.org">http://trac.streamlinedframework.org</a>.

FEATURES

* easily test plugins/extensions using a require from your test_helper.rb and a require in your RakeFile
* rake tasks to test against a specific version of Rails, or all versions of Rails available locally as Gems

TODOs:

* enable multi_rails testing in a plain ole' Rails app -- this is difficult right now because of the Rails boot process
* improve docs on how to override what files are required by  multi_rails 
* test against Rails versions that are just checked out, and not installed via Gems

REQUIREMENTS:

* Ruby 1.8.5 or higher
* Rubygems
* Rails 1.2.1 or higher
* at least one copy of Rails installed via rubygems.

Changes:

0.0.2 / Tuesday; October 23, 2007

* first public release!
* add link to email group
* improve docs
* add hook file to load rake tasks when used as a gem
* change the env var for specifying the rails version under test to
avoid name conflicts
