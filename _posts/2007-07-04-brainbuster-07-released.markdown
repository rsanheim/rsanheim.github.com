--- 
wordpress_id: 327
layout: post
title: BrainBuster 0.7 released
wordpress_url: http://www.robsanheim.com/?p=327
---
BrainBuster is a logic captcha plugin for Ruby on Rails.  The 0.7 release has been completely overhauled to have a much less obtrusive approach using only filters, instead of requiring code changes to actions.  It also features enhanced security, tests (!), and overall goodness.

If you are upgrading, PLEASE see the readme - the old modules are deprecated and you should transition to the new filters if you want to use this release.

BrainBuster is can be seen in action on the official Rails wiki, or on the Madison Rails wiki (http://madisonrails.com).

This version also sees the move to google project hosting:

Homepage: <a href="http://code.google.com/p/robsanheim/wiki/BrainBuster">http://code.google.com/p/robsanheim/wiki/BrainBuster</a>
SVN Repository:  <a href="http://robsanheim.googlecode.com/svn/trunk/brain_buster">http://robsanheim.googlecode.com/svn/trunk/brain_buster</a>
Mailing List: <a href="http://groups.google.com/group/brainbuster-discuss">http://groups.google.com/group/brainbuster-discuss</a>
Readme: <a href="http://robsanheim.googlecode.com/svn/trunk/brain_buster/README">http://robsanheim.googlecode.com/svn/trunk/brain_buster/README</a>

How to Install:

<pre><code>script/plugin install http://robsanheim.googlecode.com/svn/trunk/brain_buster
script/generate brain_buster_migration
rake db:migrate
Now add the filters to the actions you want to protect, add the
captcha form (_captcha.rhtml) to the view, and you are all set to bust
brains.</code></pre>

Please join the mailing list for questions or help.  
