--- 
wordpress_id: 394
layout: post
title: Scp or rsync failing with no error message?  Check your startup scripts...
wordpress_url: https://robsanheim.com/2008/09/15/scp-or-rsync-failing-with-no-error-message-check-your-startup-scripts/
---
The other day I was having issues trying to scp/rsync data, with no real error message to try and debug things.  Turns out that any output produced by your startup scripts will break rsync/scp hard.  I had some simple 'echo' statements print when different scripts were being loaded...turns out scp/rysync don't like that.

My capistrano task was a very simple call out to the 'get' helper, which just uses scp under the hood.  The task ran and looked as if it completed, only nothing was ever transferred and the scp progress bar never came up.  Sometimes it would block and do nothing, which was real fun, too.

The solution was simple - change all the <a href="https://github.com/relevance/etc">bash scripts</a> we use to not output any echo anything when running.  I deployed the new scripts to all servers I needed to scp with, and the issue was resolved.

Since this is a <a href="https://www.openssh.org/faq.html#2.9">known issue in the faq</a>, it won't be fixed or improved with a better error message.  It's just something you need to be aware of and work around, either via detecting if the session has an interactive terminal before sending output or removing your output statements altogether from you startup scripts.
