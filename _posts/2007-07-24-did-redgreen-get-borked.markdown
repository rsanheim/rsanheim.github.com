--- 
wordpress_id: 330
layout: post
title: Did redgreen get borked?
wordpress_url: http://www.robsanheim.com/2007/07/24/did-redgreen-get-borked/
---
I recently had to reinstall all my favorite gems and tools on a powerbook, and desired colored test goodness.  So after bringing in <a href="http://errtheblog.com/post/15">redgreen</a> and zentest gems, amongst others, I saw the following:

<pre><code>
rob@fixx:~/src/relevance/pharminst/trunk$ rake|redgreen
-bash: redgreen: command not found
^Crake aborted!

rob@fixx:~/src/relevance/pharminst/trunk$ rake|rg
/opt/local/lib/ruby/gems/1.8/gems/redgreen-1.2.2/bin/rg:6: can't convert nil into String (TypeError)
        from /opt/local/bin/rg:16:in `load'
        from /opt/local/bin/rg:16
^Crake aborted!
</code></pre>

On looking at the code, I see that the command line filter was renamed to 'rg', only now it just throws that error see above if i filter a test run through it.  Doing a 'require redgreen' in my autotest file (.autotest) still works, sort of, as its just the seperator bar that gets colored and not the actual assertion line. 

Did I mess something up on install, or has anyone else noticed this?
