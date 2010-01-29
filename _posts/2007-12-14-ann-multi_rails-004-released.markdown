--- 
wordpress_id: 356
layout: post
title: "[ANN] multi_rails 0.0.4 Released"
wordpress_url: http://robsanheim.com/2007/12/14/ann-multi_rails-004-released/
---
	<p>MultiRails lets you test your Rails plugin or app against many versions of Rails in one sweep.</p>


<h4><span class="caps">DESCRIPTION</span>:</h4>

	<p>MultiRails allows easy testing against multiple versions of Rails for your Rails specific gem or plugin.  It also has tentative support testing Rails applications against multiple versions of Rails.</p>


<p>Use MultiRails to hook in Rails 2.0 testing in your continuous integration.  Still working on Rails 2.0 support?  Use MultiRails to see where your test suite falls down against the latest and greatest versions of Rails.</p>

	<p>MultiRails was initially developed by members of Relevance while developing Streamlined against edge Rails.  To see how Streamlined uses MultiRails, go to <a href="http://trac.streamlinedframework.org">http://trac.streamlinedframework.org</a>.</p>


<h4><span class="caps">FEATURES</span>:</h4>




	<ul>
	<li>easily test plugins/extensions using a require from your test_helper.rb and a require in your RakeFile</li>
		<li>rake tasks to test against a specified version of Rails, the latest version, or all versions</li>
		<li>tentative support for testing plain Rails apps against multiple versions of Rails</li>
		<li>Uses rubygems for version management of Rails</li>
	</ul>


<h4>TODOs:</h4>




	<ul>
	<li>improve docs on how to override what files are required by multi_rails</li>
		<li>maybe add ability to load plain Rails versions&#8212;ie checked out copies not in RubyGems</li>
	</ul>


<h4><span class="caps">NOTES</span>:</h4>




	<ul>
	<li>(<i>For Rails apps only</i>) multi_rails will rename your vendor/rails directory to vendor/rails.off if it finds one within your rails app.  We have to do this to make Rails fall back to RubyGems rails.  Multi_rails will rename back to the correct vendor/rails when done testing, so it will not interrupt your app in normal use.</li>
		<li>(<i>For Rails apps only</i>) multi_rails needs to add a line to top of your environment.rb to hook into&#8212;see the instructions below for more details</li>
	</ul>


	<p>Changes:</p>


<h4>0.0.4</h4>




	<ul>
	<li>Change the all task so that the build will run through all rails versions, even if one of them fails, but at the end
  the failing versions are printed and we abort.  Thanks to Evan Weaver for initial patch and idea.</li>
		<li>display the rails gem from the load path as a sanity check right after we gem/require</li>
		<li>add autotest railsplugin discovery, so I can use autotest to test multi_rails</li>
		<li>various rake tweaks to make release easier and more automated</li>
	</ul>


	<ul>
	<li>< <a href="http://multi-rails.rubyforge.org/">http://multi-rails.rubyforge.org/></li>
	</ul>

	<p>by Relevance, <a href="http://thinkrelevance.com">http://thinkrelevance.com</a> - Rob Sanheim &#8211; MultiRails lead</p>
 

