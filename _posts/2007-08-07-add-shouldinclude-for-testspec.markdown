--- 
wordpress_id: 334
layout: post
title: Add "should.include?" for test/spec
wordpress_url: http://robsanheim.com/2007/08/07/add-shouldinclude-for-testspec/
---
I have done the following one too many times:

[ruby]collection.should.include?(object)[/ruby]

Only to have it fail because <a href="http://errtheblog.com/post/4268">test/spec's</a> should doesn't know about include? (or .not.include?)  

<strong>However</strong>, as <a href="http://errtheblog.com/">Chris</a> points out in the comments, test/spec does allow .should.include (without the "?"), but does not have a should.not version of it.  So the following adds a alias with the question mark, and also adds the should.not complement.

[ruby]module Test::Spec::Rails::ShouldInclude
  def self.included(base)
    base.class_eval { alias_method :include?, :include }
  end
end

module Test::Spec::Rails::ShouldNotInclude
  def self.included(base)
    base.class_eval { alias_method :include?, :include }
  end
  
  def include(value)
    msg = build_message(@message, "< ?> expected to not include ?, but it did.", 
                        @object, value)
    assert_block(msg) { !@object.include?(value) }
  end
end

Test::Spec::Should.send(:include, Test::Spec::Rails::ShouldInclude)
Test::Spec::ShouldNot.send(:include, Test::Spec::Rails::ShouldNotInclude)
[/ruby]

(updated 8/8)
