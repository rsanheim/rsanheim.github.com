--- 
wordpress_id: 391
layout: post
title: Notes on testing Bj (Background Job)
wordpress_url: https://robsanheim.com/2008/07/10/notes-on-testing-bj-background-job/
---
Some thoughts and random notes on testing <a href="https://codeforpeople.rubyforge.org/svn/bj/trunk/README">Bj</a> within a Rails integration test (or spec).

* You have to turn transactions off for the scope of the test, or suffer very confusing issues, since Bj itself wraps the job submittal within a transaction.  The way I did this was just overriding the use_transactional_fixtures method in the one specific spec.

```ruby
describe Foo
  def self.use_transactional_fixtures
    false
  end
```

* Remember, bj = **background** job.  This may seem obvious, but whatever you submit to bj will be running in an entirely different process, so in our spec you need to wait for that job to complete before trying to assert things.  You can do something as simple as this:

```ruby
MAX_TIME = 10.0
    seconds = 0.0
    while(job.pending?) do
      job.reload
      seconds += 0.5
      sleep 0.5
      raise if seconds > MAX_TIME
    end
# normal assertions here
```

This gives your job up to 10 seconds to finish, and will timeout if it takes too long, which usually means something has gone wrong.

* You now have to watch multiple logs to figure out what is going on.  So tail your test.log and tail the bj log as well, and run the script in isolation to make sure you understand where exceptions and syntax errors will go.  I wasted some time scanning logs when I really need to check the job.stderr field that bj populates, so be sure to output that for common test failures.</li></ul>

Overall, I've been pleased with bj, besides some open questions I've still been working out by perusing the source.  Check it out if you need a easy to use persistent job queue.
