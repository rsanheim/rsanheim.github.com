--- 
wordpress_id: 260
layout: post
title: Code worth Stealing From Ruby 1.8.5 - pretty_inspect
wordpress_url: http://www.robsanheim.com/?p=260
---
If you look at the <a href="http://eigenclass.org/hiki.rb?ruby+1.8.5+changelog">changelog</a> for Ruby 1.8.5, there is a note on the addition of a wonderful little helper method for inspecting objects: Kernel#pretty_inspect.  If you work in irb or script/console, you are probably familiar with <a href="http://www.ruby-doc.org/stdlib/libdoc/pp/rdoc/index.html">PrettyPrint</a> (aka pp) for turning this:

[ruby]hsh => {:nested=>{:hi=>"i'm a nested hash, yo!!"}, :bar=>"this is a bar", :foo=>"this is a foo"}[/ruby]

into this via pp(hsh):

[ruby]
hsh => {:nested=>{:hi=>"i'm a nested hash, yo!!"},
 :bar=>"this is a bar",
 :foo=>"this is a foo"}
[/ruby]

In fact, you probably have 'require "PP"' in your .irbrc, so that its loaded by default.  The problem with pp is that it sends to stdout, so it can't be used in a "real" program where you want things sent to a log file or some other stream.  If you try to use pp within Rails, it will just bomb out.  

What pretty_inspect does is simply allow you to say obj.pretty_inspect, and direct the nice output to wherever you want.  So now in Rails you can do:
[ruby]logger.debug("post object: #{post.pretty_inspect}")[/ruby] and get:
[ruby]#<post :0x2708914
 @attributes=
  {"to_ping"=>"",
   "comment_status"=>"open",
   "post_category"=>"0",
   "post_modified"=>"0000-00-00 00:00:00",
   "guid"=>"http://url.com/post/",
   "menu_order"=>"0",
   "post_name"=>"",
   "post_author"=>"11",
   "post_modified_gmt"=>"2006-08-28 19:55:31"....[/ruby]
</post>

Now, unless your ready to move your production system to ruby 1.8.5, you don't have this by default.  Given Ruby's open classes, however, you can just add it in.  For rails, add the following to your environment.rb (or whever you add core extensions):
[ruby]module Kernel
  # returns pretty string representation of any object, similiar to pp(obj) but more oo and easier to send to any output
  def pretty_inspect
      PP.pp(self, '')
  end
end[/ruby]

Which also happens to be the <a href="http://www.ruby-doc.org/core/classes/Kernel.src/M003281.html">implementation</a> in Ruby 1.8.5.  From seeing the code, we could've done this with pp all along, but the message to send isn't all that obvious.  That second empty parameter means "send the output to a string instead of a %> (stdout)".  

Of course, once you do upgrade ruby, you can just remove the modification and continue on with easier to read log output.

<strong>update: </strong>After more testing, this still doesn't seem to work 100%  For instance, some objects get printed nice (a simple AR object for instance), but it seems objects found via assocations don't.  Any ideas on how to just always get nice, line-breaking output would be appreciated.
