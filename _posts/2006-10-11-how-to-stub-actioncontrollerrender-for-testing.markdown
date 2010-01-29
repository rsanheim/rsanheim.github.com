--- 
wordpress_id: 276
layout: post
title: How to Stub ActionController#render for Testing
wordpress_url: http://www.robsanheim.com/?p=276
---
Sometimes you just want to ensure that render will get called with the correct parameters in a test.  Say, for instance, if you have your own special site_render method that examines subdomains or  other info about the current request, and then does the real render based on that.  This little test helper will override the render method to just return the options hash it was called with in a block, and then it will restore the original method to allow other functional tests to work correctly:

[ruby]
# stub out render to just return the options hash it was called with, to make it testable
  def stub_render_method
    @controller.class.class_eval do  
      def render(options = nil)
        options
      end
    end
    yield
  ensure
    @controller.class.send(:remove_method, :render)
  end
[/ruby]

Call it like so, with a made up "special_render" that takes some params and then calls render based on that:
[ruby]
    stub_render_method do
      assert_equal({:partial => "foo/baz/about"}, @controller.special_render(:baz => true, :partial => "about"))
      assert_equal({:partial => "foo/doop/about"}, @controller.special_render(:doop => true, :partial => "about"))
      # bad parameter, render gets called with default params and probably an error message
       assert_equal "",    @controller.special_render(:partial => "unknown_bad_parameter") 
    end
[/ruby]

Easy.
