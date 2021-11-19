--- 
wordpress_id: 316
layout: post
title: All Ruby and Rails APIs suck (but its getting better)
wordpress_url: https://www.robsanheim.com/?p=316
---
All the online APIs for Ruby and Rails suck.  Thats been a given for a long time.  Note that I'm not talking about the actual Rails Rdoc content itself - the <a href="https://blog.caboo.se/articles/2007/3/27/documentation-project-patches-are-in">doc project</a> patches continue to roll in, and the HackFest also saw many doc patches merge in.  The Ruby Rdoc content, well, a lot of is still pretty spotty.  

By online APIs, I'm referring to the web front ends to the rdoc.  The default Rails api site (<a href="https://api.rubyonrails.org/">https://api.rubyonrails.org/</a>) is clumsy, has no search, uses frames, and has many methods hidden since they are #nodoc'ed.  Its probably out of date, too, but there really isn't a way to tell what Rails version its actually from.  The <a href="https://caboo.se/doc.html">caboose docs</a> at least removes the #nodoc, but the search box is pretty much broken, and the interface is still just as bad.  <a href="https://railsmanual.com/">Rails Manual</a> adds annotation support (which is pretty much unused), has a little bit better search, but is still out of date.  Its also getting clobbered by spammers now, so I guess Rannotate should integrate a captcha (<a href="https://robsanheim.com/brain-buster">natch</a>).  <a href="https://labs.parkerfox.co.uk/ruby.search/">Ruby.search</a> combines a few api sources and has a nice little ajaxy search, except that it still doesn't work right (try searching for "activerecord" or "base").  Also, there is no Ruby 1.8 api, just the PickAxe, which is Ruby 1.6.  Finally, there used to be www.railshelp.com and rails.outertrack.com, but both are dead now.  To paraphrase the Geto Boys, pour some brew throughout the crew to remember the homies that left us.

"Are you just going to criticize, Rob?  PDI!" Fine.  I'm going to offer my ten point plan for the Totally Radical Rails and Ruby Documentation Engine (.com):

<ol>
<li>Better content.  The doc patches should keep coming in, whether its from the doc project or the rest of the community.</li>
<li>A better UI.  Rails brain is a good first step for this, but there is still lots of room for improvement.  The search results should be cached in javascript for speed.  Keyboard shortcuts should be expanded for things like page up, page down, switching to different methods in the main pane, and shift-tabbing between the options on the left.  Something like "my favorites" could save the top 10 classes I always go to, for easy access to the APIs I use most.
</li>
<li>Annotations.  <a href="https://php.net/">Php.net</a> is often pointed to as the holy grail for this, but I gotta tell ya - the user comments there are a mess.  There is a ton of good content, but also a lot of crap from developers who don't know what they are talking about.  Its also just plain difficult to follow the conversation in any of the more active pages.  So take the php.net model of having one official site where <strong>all</strong> annotations go, add a better UI and some sort of peer review system like reddits, and now you're talking.  See also the <a href="https://www.djangobook.com/en/beta/">django book</a> for some of this.</li>
<li>A clear statement of what version is covered, along with links to older version.  See <a href="https://www.djangoproject.com/documentation/">django.</a> again.  If you haven't look at the django docs you really should.
</li>
<li>Links on each method, class and file to search for "foo" on the Rails list, Ruby blogs, snippets sites, delicious, etc.  Embrace the rest of the web and the many APIs and discussion elsewhere.</li>
<li>Integrate core Ruby and the stdlib.  If you aren't learning the core libraries, you aren't taking full advantage of the platform.  The core Ruby docs are just about as bad as the core Rails docs, and it makes sense to have an option to search both or either alone.</li>
<li>An active resource API for painless interoperability.</li>
<li>A downloadable, offline version.  Not only for offline work, but the speed of offline browsing can't be beat.</li>
<li>A liberal open source license so the community can rally around it and the core team can support it.  If there are five competing doc projects, none of them will get the discussion (in annotations) or then community to make things happen.</li>
<li>CSS from top designers - if it looks cool and has sexy syntax coloring, it will be more fun to use.</li></ol>

So.  Lets have a hack night at Rails Conf, and make it happen.  I get to Portland on Monday, so I'll have some free time.  Rock n roll McDonalds?
