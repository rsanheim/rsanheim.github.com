--- 
wordpress_id: 295
layout: post
title: BDD in Rails - test/spec and rspec
wordpress_url: http://www.robsanheim.com/?p=295
---
<img src='/wp-content/bdd_survival.jpg' alt='bdd survival' />

I've been playing a bit with <a href="http://chneukirchen.org/blog/archive/2006/10/announcing-test-spec-0-2-a-bdd-interface-for-test-unit.html">test/spec</a> lately in attempts to start doing more BDD.  I've been following RSpec, the better known Ruby BDD library for awhile, but decided against it since it just doesn't look practical for use in an established project with around ~400 test cases.  It also seems that development is very active to keep up with edge rails, but ultimately a sure path to frustration as little changes in edge break the rspec plugin where they dealing with Rails internals.  There just isn't time to convert old style test cases to rspec, and there isn't time to track down bugs due to conflicts between rspec, the rspec rails plugin, and bleeding edge Rails.  Also, why didn't Rspec just use <a href="http://mocha.rubyforge.org/">Mocha/Stubba</a> -- whats up with that?

So back to test/spec.  Test/spec is small interface that sits on top of test/unit and adds "specify", "context", and "should" that just work inside normal test cases.  So most of the specs I've written looked very similiar to rspec, except that they can freely mixed with legacy test cases without issue.  Using the "context/specify" block format for specifications does break textmate integration for running specific test cases, and also trips up autotest a little bit, but those issues could probably be fixed easily.  Test/spec doesn't attempt to tie into Rails at all, so you don't get nice Rails specific should assertions, but they are <a href="http://weblog.techno-weenie.net/2006/11/24/test-spec-kicks-simply_bdds-ass">easy enough</a> to add.  Plus you don't have to worry about test/spec breaking when Rails 2.0 deprecates your favorite assertions.

I did have a minor annoyance where I had to declare fixtures (or other class level stuff) both in the normal top level and inside context blocks if mixing test cases and specs.  Example:

[ruby]class SearchControllerTest < Test::Unit::TestCase
  fixtures :users  # fixture here 

  context "routing" do 
    fixtures :users # and here
    
    specify "i am the walrus" do
    end
  end
  
  def test_should_go_to_bed_earlier
    my.bedtime.should.be.before.2.am
  end
[/ruby]
    
Again, a minor thing, and I'm sure there is ruby magic that could be used to get around it.  

Overall, I do find the specs read easier, which I think is the main thing and what really makes any of this stuff worth doing.  Once you start saying "test_should" instead of "test_blah" you are already 80% of the way there in your head, so its really just a matter of getting the specs to read well.  Lately I've just been using "foo.should.not.be.nil" inside normal test cases, so I can use the tools I like and still think "should" instead of "assert".  I really dislike the.dot.notation and plan on hacking it to allow underscores, or maybe strings like Rick is doing.

So, yay on test/spec and doing BDD with less code, even for "legacy" Rails projects with a lot of test cases.  Hopefully rspec will really be ready for Rails production work after 1.2 comes out and things settle down.  For now, test/spec + mocha/stubba it is.
