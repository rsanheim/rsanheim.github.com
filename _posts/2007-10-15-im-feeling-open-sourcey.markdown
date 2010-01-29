--- 
wordpress_id: 340
layout: post
title: I'm feeling open sourcey...
wordpress_url: http://robsanheim.com/2007/10/15/im-feeling-open-sourcey/
---
Got some open source updates and releases coming soon:

<ul>
<li>My logic captcha plugin for Rails, <a href="http://code.google.com/p/robsanheim/wiki/BrainBuster">BrainBuster</a>, has recently been <a href="http://www.railsonwave.com/railsonwave/2007/10/9/brainbuster-globalized">globalized</a> by one creative user.  I'd like to incorporate something into the next release to make it easy for people to extend the plugin in ways like this, but I'd like to avoid adding a "lang" specific column to the table.  It might make sense to completely remove the ActiveRecord model completely, and just use a PORO (plain ole' ruby object) for the questions and answers.  Then users could provide a backing AR model if they like, or just use a plain old object.</li>

<li>At <a href="http://relevancellc.com">Relevance</a> we have been hard at work updating Streamlined to get it compatible with edge Rails, which is all the more important with Rails 2.0 coming.  Out of this effort we could have a gem coming that should make it much easier for plugin developers to test against many versions of Rails, and possibly also test apps against different versions of Rails.  Watch this space or the <a href="http://relevancellc.com/blog">Relevance blog (warning: ugly)</a> for an announcement coming soon.</li>

<li><a href="http://muness.blogspot.com/">Muness</a> got an improved version of <a href="http://rubyforge.org/frs/shownotes.php?group_id=1024&release_id=8105">turn</a> into our internal tools at Relevance that displays hyperlinks back to the failing line in Textmate.  Its really helpful when you are dropping back into terminal to run tests, and I can picture it being a great workflow to combine with autotest.  We just need to get some sort of auto-test-spec, maybe using <a href="http://nubyonrails.com/articles/automation-with-rstakeout">rstakeout</a>.  If we are able to get our modified version of turn to a more stable state, we may just release it.</li>
</ul>
