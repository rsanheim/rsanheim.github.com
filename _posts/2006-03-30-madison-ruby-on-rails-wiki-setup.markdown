--- 
wordpress_id: 218
layout: post
title: Madison Ruby on Rails wiki setup
wordpress_url: https://www.robsanheim.com/?p=218
---
Finally got <a href="https://dev.rubyonrails.org/browser/tools/i2">i2</a> setup on dreamhost for the <a href="https://www.madisonrails.com">Madison Ruby on Rails Wiki</a>.  Most of the trouble was due to human error, of course.  There is still an issue where it seems Rails uses the cached version of a page when it should really hit the database to pick up changes.  Not sure if thats an i2 issue or a setup issue.  Of course now I'm not sure if I should've done all this with <a href="https://instiki.org/show/HomePage">instiki</a>, but it seems i2 should be fine for our modest needs.

A few notes from the whole ordeal:
<ul>
<li>stick with the dreamhost convention to save a lot of trouble - ie. bring your app into "~/www.mydomain.com/" to avoid dealing with annoying rewrite issues.</li>
<li>use i2 from alexey's branch, as it has some fixes and also has a working version of RedCloth in the lib folder, which can save some trouble dealing with the broken version (3.04)</li>
<li>to migrate to production, the command is "rake environment RAILS_ENV=production migrate" - rake tries to migrate to development by default</li>
<li>i2 saves plain .html copies in the public/wiki folder by default, which is where I'm having problems right now...</li>
<li>i2 appears to work fine with Rails 1.1 on XP from my very limited testing - dunno about linux yet</li>
</ul>

If anyone has any ideas on the i2 cache issue, please drop a comment.
