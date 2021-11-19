--- 
wordpress_id: 420
layout: post
title: CapGun 0.2.0 - now with all Git commits since the last release
wordpress_url: https://robsanheim.com/?p=420
---
<a href="https://thinkrelevance.com">Relevance</a> has released <a href="https://github.com/relevance/cap_gun/tree/master">CapGun 0.2.0</a> to GitHub and Rubyforge.

We've added more Git knowledge to this release, courtesy some great work from <a href="https://muness.blogspot.com/">Muness</a>.  Your deployment notifications will now contain the branch they were deployed from and a list of all revisions included in the deployment (since the last deploy, of course).  

There was also a overhaul to the internals.  Muness refactored all the email logic to a presenter, so it should easy to change the notification email to your liking.  CapGun now uses Jeweler and Micronaut, to match the rest of the standards for Relevance open source.  

Keep us honest by checking the <a href="https://runcoderun.com/relevance/cap_gun">build status</a> on RunCodeRun, and file feature requests and bug reports on <a href="https://github.com/relevance/cap_gun/issues">Github Issues.</a>
