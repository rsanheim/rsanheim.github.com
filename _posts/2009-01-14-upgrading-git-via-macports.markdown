--- 
wordpress_id: 414
layout: post
title: Upgrading git via MacPorts
wordpress_url: https://robsanheim.com/?p=414
---
<a href="https://git-scm.com/">Git 1.6.1</a> was released at Christmas, and if you are still on 1.6.0 or lower its well worth upgrading.  MacPorts is the way to go for Git on the Mac - the ports team has been awesome in keeping up with the latest versions.  Here's how I upgrade:

First, make sure you have the latest portfiles:

<code>sudo port sync</code>

Deactivate any preexisting versions - not sure if this is strictly necessary, but I've seen failures when I don't.

<code>sudo port deactivate git-core</code>

Install the new hotness, with all optional add-ons.

<code>sudo port install git-core +svn+bash_completion+doc</code>

Verify it:

    git --version

    => git version 1.6.1

Note that there is a MacPorts 'upgrade' command, but I've seen it fail to actually upgrade things from time to time.  Doing the install this way always works for me.
