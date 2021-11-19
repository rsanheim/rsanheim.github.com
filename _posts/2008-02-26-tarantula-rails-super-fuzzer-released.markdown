--- 
wordpress_id: 373
layout: post
title: Tarantula, Rails super-fuzzer, released
wordpress_url: https://robsanheim.com/2008/02/26/tarantula-rails-super-fuzzer-released/
---
Stu has <a href="https://blog.thinkrelevance.com/2008/2/26/tarantula-vs-your-rails-app">finally released Tarantula</a> over on the main Relevance blog.  Tarantula is probably the most exciting open source release Relevance has put out since I've joined the company about half a year ago.  It basically will crawl your app intelligently, try putting garbage into forms and query params, and give you a nice looking report of what breaks and what doesn't.  It can also validate html as it goes.  

We have a lot of good ideas and plans for many more things this tool can do - one big thing I'd like to see is the ability for it to run in a black box mode against your real app (in a staging env, of course) in addition to a running as a Rails integration test.  

<a href="https://www.flickr.com/photos/robsanheim/2293635887/" title="Tarantula sample by robsanheim, on Flickr"><img src="https://farm3.static.flickr.com/2329/2293635887_93bc920eb9_m.jpg" width="240" height="181" alt="Tarantula sample" /></a>
