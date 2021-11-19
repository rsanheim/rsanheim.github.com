--- 
wordpress_id: 289
layout: post
title: Updating a Rails App for 1.2 - Notes and Tips
wordpress_url: https://www.robsanheim.com/?p=289
---
Recently finished updating a app for Rails 1.2, the whole process wasn't too painful and its nice to see core get serious about removing cruft.  Here are a few notes on the process:

	<ul>
		<li>Do the easy changes first &#8211; @request, @params, @flash, etc should all go away.  Note that you still need @request in your test cases, so if you use a global find/replace limit it to your app folder.  If you see a flood of warnings about @request, @params, etc, and you <strong>know</strong> that you aren&#8217;t using them in indicated test, it probably means you are calling a missing method or something similiar.  Not sure why that happens, something that goes crazy in method_missing perhaps.</li>
	</ul>

	<ul>
		<li>Some assertions aren&#8217;t directly replacable with what the deprecation message indicates &#8211; you may have to dig into the source for a bit more clue on what the assertion was actually doing. (see <a href="https://dev.rubyonrails.org/browser/trunk/actionpack/lib/action_controller/assertions/deprecated_assertions.rb">deprecated_assertions.rb</a>)</li>
	</ul>

	<ul>
		<li>If you like some of the deprecated assertions, you can always add them to your own test_helper.  I did this with assert_success because its common enough that I don&#8217;t want to use [ruby]assert_response :success, "blah"[/ruby] everywhere.</li>
	</ul>

	<ul>
		<li>Public methods in application controller are no longer accessible via routing by default &#8211; so if you have a login action or something that used to work, it won&#8217;t anymore.</li>
	</ul>

	<ul>
		<li>I always forget if its &#8220;deprEcation&#8221; or &#8220;deprAcation&#8221;.  I hate that.</li>
	</ul>

	<ul>
		<li>We had a bunch of warnings due to object level transactions that came from our user system &#8211; we used one of the early plugins for that.  Since we will probably replace that system anyways, I just used the miracle of <a href="https://caboo.se/doc/classes/ActiveSupport/Deprecation.html#M004787">Deprecation::silence</a> to get rid of the warnings.  Obviously you don&#8217;t wanna go overboard with that, as you&#8217;ll be out of luck when 2.0 comes around&#8230;</li>
	</ul>

	<ul>
		<li>Had some issues with HelperTestCase freaking out, using a mix of Geoffrey&#8217;s plugin and some handwritten hacks.  Ended up just rewriting the whole thing, its cleaner but still not perfect.  Why isn&#8217;t something for testing helpers in core?</li>
	</ul>

	<ul>
		<li>The blogs and trac say assert_tag is deprecated for assert_select, but its not actually deprecated anywhere in the code.  Assert_select is much nicer, though, and I think that was just an oversight.  For doing the super simple case of &#8220;assert this substring is on the page somewhere&#8221;, do this: [ruby]assert_select *, :content => "give me all your pancakes!"[/ruby] that replaces [ruby]assert_tag :content => "foo bar biz"[/ruby]</li>

<li>Don't miss <a href="https://www.railtie.net/articles/2006/11/02/deprecations-in-rails-1-2">this list</a>, and of course the <a href="https://cheat.errtheblog.com/s/deprecated/">cheat sheet</a> if you swing that way - tho the cheat sheet needs some love, its missing some stuff.
	</li></ul>
