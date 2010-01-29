--- 
wordpress_id: 243
layout: post
title: Mick Clark's Testing Session from Rails Conf
excerpt: Mike Clark's testing session disappointed me
wordpress_url: http://www.robsanheim.com/?p=243
---
(little late in posting this...this is from the last day at <a href="http://railsconf.org">RailsConf</a>)
I was a bit disappointed in Mike Clark's talk on testing.  It had a lot of very intro level, beginner type material.  I would expect that from a No Fluff Just Stuff or user group meeting, but at RailsConf?  Isn't it safe to assume a higher level of basic knowledge at a conference like this, as I would guess at least 75% of the attendees are experienced refugees from other languages or long-time rubyists.  Similiar to "Intro to Ajax" type material, I think we can move past things like "this is a unit test", "this is how asserts work", etc.  

On the other hand, it was a general session in the ballroom with the whole conference there, so I can understand why he went for the basic, foundational material.

He went on to cover transactional fixtures, functional testing, mocks, and integration tests with DSL's.  He discussed a few tips at the end to decrease coupling, like using named routes and accessing fixtures by name, not id.  Decent stuff, I just wish there was a lot more of it.

Here are some of the things I would've liked to see:
<ul><li>how can I unit test things in controllers in a true isolated manner?</li>
<li>why fixtures <strong>suck</strong>, and what can be done about it</li>
<li>a discussion of the terms used in Rails-testing vs TDD in Java/C# land</li>
<li>how to test helpers or stuff in your /lib directoy</li>

<li>tools to use locally - ie autotest, stakeout, how about some better feedback then "...F..." on the command line?  I want colors and sound options</li>
<li>when/how to break apart the generated test cases when they get too large</li>

Maybe next year...</ul>
