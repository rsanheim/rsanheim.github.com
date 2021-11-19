--- 
wordpress_id: 238
layout: post
title: Testing the ApplicationController in Rails
wordpress_url: https://www.robsanheim.com/?p=238
---
Not sure why this test case isn't generated right away, but here it is:

[ruby]require File.dirname(__FILE__) + '/../test_helper'
require 'application'

# Re-raise errors caught by the controller.
class ApplicationController; def rescue_action(e) raise e end; end

class ApplicationControllerTest < Test::Unit::TestCase
  
  def setup
    @controller = ApplicationController.new
  end
  
# your test here
  def test_truth
    assert true
  end
end[/ruby]
