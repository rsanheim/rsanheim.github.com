--- 
wordpress_id: 284
layout: post
title: Whats wrong with this method_missing?
wordpress_url: https://www.robsanheim.com/?p=284
---
A coworker who shall remain nameless had this method missing implementation in a module that got mixed into the app helper.  This tricked me up for longer then it should, mostly because I hadn't synced up in awhile and so assumed the problem was in changes I made.  I don't know if it would break anything in production, as I never go that far - a whole bunch of failing tests stopped me before I got that far.

[ruby]
module AdRender
# gets included into ApplicationHelper, which gets included into the entire view layer, etc...

  def method_missing(methodname, *args)
    if methodname =~ /^render_/
      methodname[/^render_/] = ''
      render_ad methodname
    end
  end
end
[/ruby]

Do you see whats wrong?
