--- 
wordpress_id: 22
layout: post
title: setting up awstats on rimuhosting (user mode linux)
excerpt: detailed steps on getting awstats setup on my rimuhosting.com account
wordpress_url: https://www.robsanheim.com/?p=22
---
My host, <a href="https://www.rimuhosting.com">Rimuhosting</a>, has <a href="https://www.mrunix.net/webalizer/">Webalizer </a>installed by default for tracking web stats.  Its a decent stat tracker, but <a href="https://awstats.sourceforge.net/">awstats </a>looks a lot nicer and seems to be a better solution.  Awstats did have some security exploits recently, but they have been fixed in the latest 6.4 release.  Here are the steps I've taken to install awstats on my account.  For the record, I'm using <a href="https://www.whiteboxlinux.org/">White Hat Enterprise Linux 3</a> via <a href="https://user-mode-linux.sourceforge.net/">User Mode Linux</a>.  Your settings and defaults could and probably will vary.  This assumes you have root access to your box and at least a little knowledge of the command line.  Use these instructions at your own risk - if you blow up your virtual private server and your dog dies in a horrible frisbee accident, I am not responsible.

I referred the following two articles a lot to get things working:
<a href="https://codeworks.gnomedia.com/westhost-introduction/setting-up-awstats/">https://codeworks.gnomedia.com/westhost-introduction/setting-up-awstats/</a>
<a href="https://cephas.net/blog/2005/06/17/awstats_installation_notes.html">https://cephas.net/blog/2005/06/17/awstats_installation_notes.html</a>

First things first - back up your apache config file - the configure script that awstats uses will modify it...

<code>cp /etc/httpd/conf/httpd.conf /etc/httpd/conf/httpd.conf.awstatsbak</code>

Download awstats 6.4 from sourceforge - pick the mirror that works best for you via sourceforge

<code>cd /download (use your normal download location)
lynx <a href="https://prdownloads.sourceforge.net/awstats/awstats-6.4.tgz">https://prdownloads.sourceforge.net/awstats/awstats-6.4.tgz</a> 
</code>

Extract the archive, rename the default install folder, and move it to the correct application folder:

<code>tar xzf ~/awstats-6.4.tgz
mv awstats-6.4 awstats
mv awstats /usr/local/</code>

Create the data directory for awstats - this is just the default location, I'm guessing you can put it wherever you want if you want to modify the config later

<code>mkdir /var/lib/awstats</code>

Change dir to the awstats app folder and run the configure script

<code>cd /usr/local/awstats/tools
perl awstats-configure.pl</code>

The configure script is pretty well explained with help text, and you can read the official docs <a href="https://awstats.sourceforge.net/docs/awstats_setup.html">here</a>.  Basically, it will check your apache log format, setup some directives for redirects to awstats, ask for your server name, and restart apache (with your confirmation, of course).  Enter your most common server name - for my site I entered www.robsanheim.com, and specified robsanheim.com as a secondary option later.

Now go check the awstats config file:

<code>vim /etc/awstats/awstats.www.domain.com.conf
LogFile="/var/log/httpd/access_log"</code>

LogFile should point to the apache log location

<code>HostAliases="domain.com domain.net domain.org"</code>

For host aliases, enter other addresses, if any, that you can get use to access your site.  You can go through this config file in more detail with help from the main dos.  You may also want to review the changes that the config script made to your apache config, just to see what it did in case you need to change anything later:

<code>less /etc/httpd/conf/httpd.conf</code>

Now run an awstats update manually to confirm things are working:

<code>/usr/local/awstats/wwwroot/cgi-bin/awstats.pl -config=yoursite.com -update</code>

You should see output similiar to:

<code>Update for config "/etc/awstats/awstats.yoursite.com.conf"
With data in log file "/var/log/httpd/access_log"...
Phase 1 : First bypass old records, searching new record...
Direct access after last parsed record (after line 4505)
Jumped lines in file: 4505
 Found 4505 already parsed records.
Parsed lines in file: 175
 Found 0 dropped records,
 Found 0 corrupted records,
 Found 0 old records,
 Found 175 new qualified records.</code>

If you got errors at that point, double check that you are using passing in the same domain name to awstats that is in the name of your config file.  So if your config file is awstats.www.boogie.com.conf, the command would be: ..."awstats.pl -config=www.boogie.com -update".

If you are past that point, you are doing good.  Now try and update via the web - point your web browser to www.yoursite.com/awstats/awstats.pl?config=yoursite.com - putting in your correct site address in both spots in the URL, of course.  If everything is golden, the update will process and you will have a nice page load similiar to <a href="https://awstats.sourceforge.net/cgi-bin/awstats.pl">this</a>.  If you get "403 Forbidden Error", here are somet things to try:

<code>chown apache.apache /var/lib/awstats
chown apache.apache /usr/local/awstats</code>

This sets the default apache user account/group as the owner of the awstats directories.  If that still doesn't do it, try the following:

<code>chmod 755 /usr/local/awstats/</code>

That will set more general permissions on the awstats directory.  I ended up doing both, but the chown is what got things working for me.

Now the next step is to setup a scheduled job to update the stats on a regular interval.  I'll tackle that in part 2...
