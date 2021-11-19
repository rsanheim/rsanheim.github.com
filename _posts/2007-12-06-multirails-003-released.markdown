--- 
wordpress_id: 351
layout: post
title: MultiRails 0.0.3 released
wordpress_url: https://robsanheim.com/2007/12/06/multirails-003-released/
---
MultiRails lets you test your Rails plugin or app against many versions of Rails in one sweep.

  rubyforge:    <a href="https://rubyforge.org/projects/multi-rails/">https://rubyforge.org/projects/multi-rails/</a>
  rdocs:        <a href="https://multi-rails.rubyforge.org/">https://multi-rails.rubyforge.org/</a>
  svn stable:   <a href="https://robsanheim.googlecode.com/svn/tags/stable/multi_rails">https://robsanheim.googlecode.com/svn/tags/stable/multi_rails</a> (gem is released from here)
  svn trunk:    <a href="https://robsanheim.googlecode.com/svn/trunk/multi_rails">https://robsanheim.googlecode.com/svn/trunk/multi_rails</a>
  mailing list: <a href="https://groups.google.com/group/multi_rails">https://groups.google.com/group/multi_rails</a>
  
<h2>Description</h2>

MultiRails allows easy testing against multiple versions of Rails for your Rails specific gem or plugin.  IT also has tentative support testing Rails applications against multiple versions of Rails.

Use MultiRails to hook in Rails 2.0 testing in your continuous integration.  Still working on Rails 2.0 support?  Use MultiRails to see where your test suite falls down against the 2.0 preview releases of Rails.

MultiRails was initially developed by members of Relevance while developing Streamlined against edge Rails.  To see how Streamlined uses MultiRails, go to <a href="https://trac.streamlinedframework.org">https://trac.streamlinedframework.org</a>.

<h2>Features</h2>

* easily test plugins/extensions using a require from your test_helper.rb and a require in your RakeFile
* rake tasks to test against a specified version of Rails, the latest version, or all versions
* tentative support for testing plain Rails apps against multiple versions of Rails
* Uses rubygems for version management of Rails

<strong>For the full docs see the <a href="https://robsanheim.googlecode.com/svn/trunk/multi_rails/README.txt">readme.</a></strong>
