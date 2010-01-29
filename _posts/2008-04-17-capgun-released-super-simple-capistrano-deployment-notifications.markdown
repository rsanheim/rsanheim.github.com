--- 
wordpress_id: 385
layout: post
title: CapGun Released!  Super simple Capistrano deployment notifications
wordpress_url: http://robsanheim.com/2008/04/17/capgun-released-super-simple-capistrano-deployment-notifications/
---
<p>Tell everyone about your releases!  Send email notification after Capistrano deployments!  Rule the world!</p>

<p>Drop your ActionMailer configuration information into your deploy.rb file, configure recipients for the deployment notifications, and setup the callback task.</p>

<p>Setup and configuration are done entirely inside your deploy.rb file to keep it super simple.  Your emails are sent locally from the box performing the deployment, but CapGun queries the server to grab the necessary release info.</p>

<p>This even includes the Net::SMTP TLS hack inside as a vendored dependancy to allow super easy email sending without setting up an MTA.</p>

<p>This is the "Rock n Roll McDonalds" release - 0.0.1.</p>

<h4>INSTALL</h4>

<ul>
<li>sudo gem install cap_gun  and gem unpack into your vendor/plugins</li>
<li>or just grab the tarball from github (see below)</li>
<li>see the readme and rdocs for more config notes</li>
</ul>

<h4>URLS</h4>

<ul>
<li>Log bugs, issues, and suggestions on Trac: <a href="http://opensource.thinkrelevance.com/wiki/cap_gun"> http://opensource.thinkrelevance.com/wiki/cap_gun </a></li>
<li>View source: <a href="http://github.com/relevance/cap_gun/tree/master">http://github.com/relevance/cap_gun/tree/master</a></li>
<li>Git clone source: git://github.com/relevance/cap_gun.git</li>
<li>RDocs: <a href="http://thinkrelevance.rubyforge.org/cap_gun/">http://thinkrelevance.rubyforge.org/cap_gun/</a></li>
</ul>

