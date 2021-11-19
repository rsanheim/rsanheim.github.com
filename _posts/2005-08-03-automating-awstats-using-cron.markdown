--- 
wordpress_id: 38
layout: post
title: Automating awstats using cron
wordpress_url: https://www.robsanheim.com/?p=38
---
This is the second part of an an article about getting awstats setup and automated.  You might be interested in <a href="https://www.robsanheim.com/2005/07/20/setting-up-awstats-on-rimuhosting-user-mode-linux/">part one.</a>

First, make sure you have cron running:

<code>ps aux | grep crond</code>

This should display at least one line that has the following:

<code>root       311  0.0  0.7  1284  112 ?        S    Dec24   0:00 crond</code>

Which means you are good to go.  Now, you are going to create a very simple shell script that will run your awstats update.  Go into your favorite text editor and enter the following:

<code>#!/bin/bash
/usr/local/awstats/wwwroot/cgi-bin/awstats.pl -config=robsanheim.com -update</code>

Note that the first line just tells the shell to use bash to intrepret the file.  I don't know if its necessary if bash is your default, but it can't hurt.  The awstats command should be the same one you used to update manually during the initial setup.  Save the file as "awstats_update".  

Now you need to make it executable and private, and we are also going to move the script file to your /usr/local/bin directory (which seems to make sense on my config, yours may vary).

<code>chmod 700 awstat_update
mv awstat_update /usr/local/bin</code>

Now, assuming the directory you moved the script into is in your path, you should be able to type <code>awstat_update</code> from any where and your stats will get updated.  Now the cron setup is the easy part, assuming you have a <code>/etc/cron.daily</code> folder.  You need to make a symbolic link to your awstat batch file in your cron.daily folder.

<code>cd /etc/cron.daily
ln -s /usr/local/bin/awstat_update</code>

Thats it!  Now when you look at the files in cron.daily, you should see the symbolic link pointing to the awstat_update like so: <code>awstat_update -> /usr/local/bin/awstat_update</code>.  Now your update will run every day at the time specified in <code>/etc/crontab</code>.

Some additional resources:
<a href="https://linuxcommand.org/index.php">linuxcommand.com</a> is great
<a href="https://en.wikipedia.org/wiki/Cron">cron at wikipedia</a>
<a href="https://adminschoice.com/docs/crontab.htm">a decent cron resource at admins choice</a>

