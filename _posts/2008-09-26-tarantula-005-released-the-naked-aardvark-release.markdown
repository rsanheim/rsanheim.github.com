--- 
wordpress_id: 395
layout: post
title: Tarantula 0.0.5 Released - the "Naked Aardvark" release
wordpress_url: http://robsanheim.com/2008/09/26/tarantula-005-released-the-naked-aardvark-release/
---
Announcing version 0.0.5 of <a href="https://github.com/relevance/tarantula/tree/master">Tarantula.</a>  

Tarantula is a big fuzzy spider. It crawls your Rails application, fuzzing data to see what breaks.  It can verify HTML validation across all your pages, ensure you don't have 404s, and pretty much anything else you want via custom handlers.

Don't let the version number fool you, we've been using Tarantula across many projects at <a href="http://thinkrelevance.com">Relevance</a> and its very stable.  This release fixed a number of annoying bugs, including namespace conflicts with other classes due to Rails dependency loading, improved gem spec with correct dependencies, and clean up on the html reporter.

Install it via the Github

<code>gem install relevance-tarantula --source http://gems.github.com</code>

or via Rails 2.1+ gem handing:

<code>config.gem "relevance-tarantula", :source => "http://gems.github.com"</code>
