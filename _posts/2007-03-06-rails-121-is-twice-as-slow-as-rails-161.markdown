--- 
wordpress_id: 302
layout: post
title: Rails 1.2.1 is twice as slow as Rails 1.1.6?
wordpress_url: http://www.robsanheim.com/?p=302
---
This seems very strange to me - look at the performance between Rails 1.1.6 and Rails 1.2.1 in <a href="http://www.alrond.com/en/2007/jan/25/performance-test-of-6-leading-frameworks/">this performance comparison.</a>  The rails code is very simple - just set an instance variable in the controller and render it in the rhtml.  How could this be so much slower in 1.2.1?  The comments are mostly in Russian, so I'd love to hear comments from someone in core on this...
