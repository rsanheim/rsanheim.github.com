--- 
wordpress_id: 390
layout: post
title: CapGun and LogBuddy updated to 0.0.5
wordpress_url: https://robsanheim.com/2008/07/06/capgun-and-logbuddy-updated-to-005/
---
Some long overdue releases of <a href="https://github.com/relevance/cap_gun">cap_gun</a> and <a href="https://github.com/relevance/logbuddy/tree/master">log_buddy</a> - both have been updated to version 0.0.5.  Both are now available as gems on github.com/relevance as well as from rubyforge.

CapGun gives you super simple deployment notifications from Capistrano.  LogBuddy gives you a log helper through all objects, and can also log the name of the thing passed in along with its value -- saving you on typing and making debugging quicker.

CapGun got a fix so it does not attempt to display the rails_env if its not defined - this should clean up any strangeness in notifications if you saw something like "my_app was deployed to ".

LogBuddy got some minor tweaks and improved specs.

Both libraries now use Echoe, since Hoe complains about readme.txt when I want to use readme.rdoc, dammit.  Both now only have a dev dependency on echoe to play nice with RubyGems 1.2.

You can install them via github or rubyforge:

```
sudo gem install log_buddy
sudo gem install cap_gun
```

or 

```
gem sources -a https://gems.github.com
sudo gem install relevance-log_buddy
sudo gem install relevance-cap_gun
```

Please log bugs or issues at our <a href="https://opensource.thinkrelevance.com/">Trac</a>.
