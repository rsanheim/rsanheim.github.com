--- 
wordpress_id: 392
layout: post
title: "Quick: Find the Bug or Gotcha with named_scope"
wordpress_url: http://robsanheim.com/2008/07/23/quick-find-the-bug-or-gotcha-with-named_scope/
---
Think fast!  Where's the bug?

[ruby]
  named_scope :active, :conditions => ["activated_at < = ?", DateTime.now.utc.to_s(:db)]
[/ruby]

Looks fine, right?  Maybe you've hit this already, and you see it immediately.  

The symptoms are that the DateTime.now always seems to be a bit off - maybe you just restarted your server and its a only a few minutes off.

The bug is that DateTime.now gets evaluated at the time the class is loaded, not when the finder is run.  What makes this easy to miss is that it will always work fine in tests and development, as everything is constantly getting reloaded there.

The fix, obvious once you've spent a combined time of over an hour trying to figure out what is going on:

[ruby]
  named_scope :active, lambda { { :conditions => ["activated_at <= ?", DateTime.now.utc.to_s(:db)] } }
[/ruby]
