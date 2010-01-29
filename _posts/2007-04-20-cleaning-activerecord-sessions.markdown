--- 
wordpress_id: 312
layout: post
title: Cleaning ActiveRecord Sessions
wordpress_url: http://www.robsanheim.com/?p=312
---
We realized recently that we never setup a job to clean up our active record sessions.  So this accounts for our database size growing rapidly:

<code><pre>mysql> select count(*) from sessions;
+----------+
| count(*) |
+----------+
|  2188080 | 
+----------+
1 row in set (24.64 sec)</pre></code>

Derp!

Not a big deal, really, except for the size its taking up for backups.  Its also kind of a pain to clean up now, since its so huge.

Many of the snippets you see for cleaning sessions look like <a href="http://www.realityforge.org/articles/2006/03/01/removing-stale-rails-sessions">this</a>:

<code><pre>CGI::Session::ActiveRecordStore::Session.destroy_all( ['updated_on < ?', 20.minutes.ago] )</pre></pre></code>

The problem with this is that <a href="http://api.rubyonrails.com/classes/ActiveRecord/Base.html#M001000">destroy_all</a> instantiates an ActiveRecord object for each record it destroys.  If you don't have callbacks on your Sessions, you don't need to do that.  Granted, if you are running this job every hour there shouldn't be much overhead.  But if you want to run the job less frequently or just want to avoid any unnecessary over head, you can use delete_all instead - here's a rake task that does just that:

<pre><code>
  desc "Clean up Active Record sessions updated over ENV['EXPIRE_AT'] (defaults to 3 weeks ago)."
  task :clean_ar_sessions => :environment do 
    time = ENV['EXPIRE_AT'] || 3.weeks.ago.to_s(:db)
    rows = CGI::Session::ActiveRecordStore::Session.delete_all ["updated_at &lt; ?", time]
    RAILS_DEFAULT_LOGGER.info "#{rows} session row(s) deleted."
  end
</code></pre>

In our case, even a straight delete by update time was way too slow, and would lock up the table for a long time (like, hours).  So I wrote a little job to clean up 100 records at a time, set to low priority (thanks Contegix), and just let that run.  If you ever have a similar backlog in produciton, make sure you run your deletes on a dev database first to see how slow it will be and what kind of lock you'll have on the sessions table.

Here is the <a href="http://pastie.caboo.se/55447">rake task</a> - the code above looks pretty crummy.
