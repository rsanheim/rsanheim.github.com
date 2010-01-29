--- 
wordpress_id: 338
layout: post
title: Overriding setup in Rail's test_helper - impossible?
wordpress_url: http://robsanheim.com/2007/09/06/overriding-setup-in-rails-test_helper-impossible/
---
Is there a way that will just work for adding common setup code to test_helper?  None of the below work:

[ruby]
  # this breaks fixtures in the acts_as_authenticated account_controller_test (but nowhere else, for some reason)...
  def setup
  end
[/ruby]

[ruby]
  # this breaks things all over the place
  def setup
     super
  end
[/ruby]

[ruby]
   # this is the way I think it _should_ work, but it breaks down in functional tests
  def setup_with_logging
    setup_without_logging
  end
  alias_method_chain :setup, :logging
[/ruby]

There is way too much magic happening in the rails test setup, particularly in fixtures.rb.  This should not be that difficult.
