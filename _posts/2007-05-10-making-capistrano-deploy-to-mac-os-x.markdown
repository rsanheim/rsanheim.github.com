--- 
wordpress_id: 318
layout: post
title: Deploying Locally to Mac OS X with Capistrano
wordpress_url: https://www.robsanheim.com/?p=318
---
Lately I've wanted to deploy locally to my mac using Capistrano.  Not for actual deployment locally, but to test some custom tasks I was working on.  Its a lot quicker and safer to run custom tasks against a local sandbox then some real server somewhere.  Writing real tests for custom tasks is basically too difficult to be worth it, so testing locally is probably the least crummy option right now.  Another side benefit of testing locally is the speed and removing the need for a net connection.

So out of the box, this won't work:
<pre><code>  role :app, "localhost"
  role :web, "localhost"
  role :db, "localhost"

  cap my_custom_task
</code></pre>

For one thing, mac's don't have sshd (the ssh server) running by default.  So first do that - go to System Preferences -> Sharing -> and enable "Remote Login".  That should start the ssh daemon.

Now if you deploy, Capistrano should be able to login but you may run into path issues, especially if you want to use gems in a custom task.  If you just want to use a very basic task locally, you might be okay here -- but if you see 'command not found' or missing libraries, you probably need to keep reading.

Capistrano runs SSH over a non-interactive shell, and by default you have an empty environment when logged into a OS X non-interactively via SSH.  To fix that, open up /etc/sshd_config in your favorite text editor.  Change the following:
<pre><code>PermitUserEnvironment yes</code></pre>
This will allow you to set the environment in your home .ssh folder.  Before you leave that file, also find these directives and make the following changes for security:
<pre><code>PermitRootLogin no
Protocol 2
AllowUsers [username here]
</code></pre>
This will turn off root login, allow only the more recent version of ssh, and explicitly allow only the one username you'll be using.  If you want to lock it down even more you should set the port to something much higher then 22, turn off password auth, and setup keys with good pass phrases.  My mac is behind a router most of the time anyways, so I'm not going to worry about it.  If you have a password of 'password' or something similiar for the account you are using, you should <strong>definitely</strong> make that stronger.

Now, create a file for you local ssh environment.  <pre><code>mate ~/.ssh/environment # or vi, or nano, etc...</code></pre>

Now add a PATH statement to that file like the following:

<pre><code>PATH=/usr/local/bin:/usr/local/sbin:/usr/local/mysql/bin:/usr/local/lib:opt/local/bin:/usr/bin:/bin:/usr/sbin:/sbin
RUBYOPT=rubygems</code></pre>

You'll probably want the /usr/local and /opt/local (for MacPorts) stuff ahead of /usr/bin so that if you use Ruby or Rubygems in your tasks, the non-broken version you installed yourself will get used.  After saving that file, go back to the system preferences and turn off ssh (remote login) and turn it back on again to pick up all changes.  Now you can run any custom task against your localhost, and it should work pretty much like a typical linux box, assuming you've installed everything locally that your have remote.  

If you still have issues, create a simple task like so:
<pre><code>task(:debug_env) { run "env" }</code></pre>

Run that locally and then run it remotely to see the differences in your environment, and hopefully that will reveal something missing from your path or maybe some env variable you need.

This was all done with Capistrano 1.4.1, as I haven't taken the plunge into the new version 2 yet.

