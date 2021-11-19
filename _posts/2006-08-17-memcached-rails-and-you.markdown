--- 
wordpress_id: 257
layout: post
title: Memcached, Rails, and You
wordpress_url: https://www.robsanheim.com/?p=257
---
Geoffrey continues the run of helpful articles with an <a href="https://nubyonrails.topfunky.com/articles/2006/08/17/memcached-basics-for-rails">intro</a> of how to implement <a href="https://www.danga.com/memcached/">memcached</a> with ActiveRecord.  I know my team will have to look into this soon, as we have some model objects that are essentially lookup objects, but need to be used for every request in some way.  Since they change rarely, we should just be able to load them once a day and let them sit in memory.  

Robot Coop's cached-model looks like it would help for this, but I don't understand why its implemented as a class instead of a module?  Seems like caching should be an implementation detail, so a module would be perfect.  Once you use cached-model you are stuck with that inheritance, and now you have to hack your way around it if you want to use some sort of common abstract class.  I feel the same way about the using a base class like "AlternateDatabase" to enable multiple database connectivity, but sometimes quick and easy wins out over the "right way"
