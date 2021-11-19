--- 
wordpress_id: 388
layout: post
title: Git lessons learned
wordpress_url: https://robsanheim.com/2008/06/06/git-lessons-learned/
---
Lessons learned from day to day use with various ruby and rails projects.

* Submodules completely suck when things get complex - I'm moving away from no submodules, and using direct exports for now until I have time to research braid or piston 2.0.  For more details on this, see <a href="https://blog.buildingwebapps.com/2008/5/20/got-git-submodules-not-a-go-go">this</a> or <a href="https://groups.google.com/group/github/browse_thread/thread/5f49768707d015dd">this post</a> on the github group.

* Use capistrano 2.2, not 2.3!  2.3 breaks git support

* Always use :remote_cache for deployments -- super fast with git

* If you have weird errors, it probably means you need to pull - when in doubt pull to make sure you have the latest

* Branch more locally - I've been burned a few times when I've started work in master and then regretted it later when I wished my work wasn't in mainline (yes, its possible to fix this after the fact, but that gets into more advanced git usage)
