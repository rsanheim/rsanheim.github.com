--- 
wordpress_id: 430
layout: post
title: Rails 2.3, JSON, and lamentations
wordpress_url: http://robsanheim.com/?p=430
---
There is a nasty gotcha in Rails 2.3 involving rendering JSON from models and a surprising change in behavior.  If you are familiar with how Rails renders xml for models, you may expect json to be very similar.  You would probably expect a top level root node followed by the attributes:

<code>{"person" => { "city=>nil, "name"=> "Foo Bar" } }</code>

It appears somewhere on the road to 2.3, the JSON encoding changed so there is no longer a top level node:

<code>{"city"=>nil, "name"=>"Foo Bar" } </code>

The end result of this change means that if you have consumers expecting JSON in a typical "Rails" format, with a top level element denoting the class, there will be pain.  We just hit this in a project when trying to use ActiveResource to consume some models exposed via standard restful actions.  

The following demonstrates how this breaks down exactly:

<code># in the backend web app
Person.create! :name => "foo"

# meanwhile, in an active resource consumer
person = Person.find(1)  # finds a model okay, but...

# the below all raise NoMethodError
# they _should_ find the attribute from the attribute hash
# and quack like an ActiveRecord model
person.name
person.age
person.any_field_on_the_model 

person.attributes # returns a hash in the format of { "person" => { "name" => "foo"...}, which is where the problem lies</code>

It appears this issue is fixed or on the way to be fixed in the 2.3 stable branch, but for now be wary of JSON support in general on 2.3 until more of the below tickets get resolved.

<strong>References:
</strong>
	<li><a href="https://rails.lighthouseapp.com/projects/8994/tickets/2584-232-activeresource-json-doesnt-send-parameters-with-root-node">the bug in question - still open</a></li>
<li><a href="https://rails.lighthouseapp.com/projects/8994/tickets/2456-activeresource-xmljson-encoding-inconsistency">xml vs json - fight!</a></li>
	<li><a href="https://rails.lighthouseapp.com/projects/8994/tickets/2753-to_json-behavior-still-different-between-rails-2321-and-rails-2-3-stable">2.3 related (?) fix that caused other issues</a></li>
<li><a href="https://rails.lighthouseapp.com/projects/8994/tickets/2196-json-encoding-breaks-when-json-gem-is-loaded-before-active-support">an unrelated JSON issue, but very annoying and has hit us on multiple projects -- require "json" considered harmful)</a></li>
