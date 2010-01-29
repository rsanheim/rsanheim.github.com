--- 
wordpress_id: 163
layout: post
title: Deployment - is it really that hard?
wordpress_url: http://www.robsanheim.com/?p=163
---
(note: this is a post from my old blog reposted here)

I'm forever amazed at how difficult deployment seems to be at shops I've worked at.  A previous employer handled deployment through a third party tool that failed routinely and required manual intervention almost daily.  I remember having to login at 2 am after the servers restarted to make sure my deployments propagated correctly - it was that fragile.  This deployment tool also handled change management, though its "unusual" interface and pessimistic locking really wasn't much better then manual control.  There wasn't even a standard process for retrieving old versions without a huge hassle.
 
Another client I have experience with also uses an unnamed third party tool for production deploys.  Like the first shop, developers dread working with the tool due because it just plain sucks.  Thank goodness they use CVS for version control, so at least some work can get done.  The deployment tool uses pessimistic locking (of course), and the Eclipse/WSAD plugin is constantly freaking out.  Some of the problems could be due to the administration, as it seems everything is setup as restrictively as possible to stop people from getting actual work done.
 
Honestly, if you are handling Java, what is wrong Ant + CVS?  Maybe Maven.  Throw in some scripts if need be.  Get everything automated and tested first, so you can type one command and the compile, test, backup, and deploy happens without any error-prone gui work or manual intervention.
 
Both of these shops use Websphere, so I suppose part of the problem may come from that.  I assume getting Ant to deploy to Websphere is more difficult then going to Tomcat.  Still, putting the time and effort in up front to do it right would far outweigh the constant struggles down the road with these expensive, universally hated tools.  There has to be some large organizations that are doing this right...
