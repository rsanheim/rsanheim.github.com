--- 
wordpress_id: 329
layout: post
title: Make Textmate's "find in project" faster in Rails projects
wordpress_url: https://www.robsanheim.com/2007/07/23/make-textmates-find-in-project-faster-in-rails-projects/
---
Textmate's "find in project" feature is great, but if you use it within any substantial Rails projects it can get very slow, especially as cruft builds up in the log folder or if you use vendor/rails.  This is easily fixed, however -- go into your textmate preferences, then "folder references", and change "folder pattern" to the following:

<strong>updated</strong>: go <a href="https://pastie.caboo.se/81736">here</a> for the code now, wordpress was stripping some slahes.

If you parse the regex, you'll see we modified the first set of exclusions (denoted by the "^").  This is why we added 'vendor/rails', 'log', and 'tmp' along side some version control exclusions that are included by default.  If you want to exclude anything else, for example all plugins ("vendor/plugins"), just add it there with a pipe ("|"), which is the reg ex equivalent of "OR".  

You'll have to reopen any projects for this to take effect, and you may have to create new projects to pick up this exclusion, if you use saved projects.  After opening a project, you can look in the project sidebar and verify that the 'log' and 'tmp folder dont' show anymore.  Find in project will be fast and friendly again.
