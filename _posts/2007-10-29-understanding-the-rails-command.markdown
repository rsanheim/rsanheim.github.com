--- 
wordpress_id: 344
layout: post
title: Understanding the Rails command
wordpress_url: https://robsanheim.com/2007/10/29/understanding-the-rails-command/
---
I ran a few quirks during the course of working on <a href="https://rubyforge.org/projects/multi-rails/">MultiRails</a> and testing against the Rails 2.0 prerelease.  

The first thing was tracking down what Rails version is actually used when you just run the "rails" command.  This is important when you have many versions of Rails installed via gems, some of which are "2.0" and others are not.  Behold:

<code>
rsanheim@Rhea:~$ sudo gem list rails

*** LOCAL GEMS ***

rails (1.2.5.7919, 1.2.5, 1.2.4.7794, 1.2.4, 1.2.3)
    Web-application framework with template engine, control-flow layer,
    and ORM.

rsanheim@Rhea:~$ rails -v
Rails 1.2.5
</code>

So I have two Rails beta gems (2.0ish) releases - those two versions that have the extra crazy version string.  Its possible that the rails command is just grabbing the highest verison, which is 1.2.5.7919, and then only displaying the major/minor/tiny version and not the actual full string.  But I digress - lets just look for ourselves:

<code>rsanheim@Rhea:~$ which rails
/opt/local/bin/rails

rsanheim@Rhea:~$ less /opt/local/bin/rails
#!/opt/local/bin/ruby
# (comments snipped)
require 'rubygems'
version = "> 0"
if ARGV.first =~ /^_(.*)_$/ and Gem::Version.correct? $1 then
  version = $1
  ARGV.shift
end
gem 'rails', version
load 'rails'
</code>

So we can be nice and explicit and give the rails command a version string so that we know just what version we are using to generate an app.  I'm not sure why this isn't documented, and why its handled in such a goofy non-standard way, but anyways...

<code>
rsanheim@Rhea:~$ rails _1.2.3_ -v
Rails 1.2.3

# bleeding edge, brah!
rsanheim@Rhea:~$ rails _1.2.5.7919_ -v
Rails 1.2.5  # wah happen?
</code>

Notice the version it reported.  Don't be fooled, its really the beta gem.  I'm guessing this is an artifact of how versioning works in rubygems, and how Rails has pushed 2.0 prereleases with version numbers of 1.2.x.y from their own gem server.  Is there any first class support within rubygems itself for marking a release as "beta - don't update to this unless explicitly asked for" ?  

