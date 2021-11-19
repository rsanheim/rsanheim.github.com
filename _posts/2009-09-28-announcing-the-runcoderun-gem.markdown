--- 
wordpress_id: 433
layout: post
title: Announcing the RunCodeRun Gem
wordpress_url: https://robsanheim.com/?p=433
---
Hook up your <a href="https://runcoderun.com">RunCodeRun</a> builds from your command line.

Install:

```
gem install runcoderun
```

Usage:

```
  cd [your-runcoderun-enabled-project]
  rcr [command] [options]
```

Right now we just support open.  This opens up your project homepage on RunCodeRun in your default browser.  It is smart enough to make a best guess at the correct owner and project name from your git config.  This requires Launchy, like the <a href="https://github.com/defunkt/github-gem">Github gem</a>.

Try it out:

```
git clone git://github.com/floehopper/mocha.git
cd mocha
opens https://runcoderun.com/floehopper/mocha in your default browser:
rcr open            
runcoderun open     # if you like to type more</code>
```

Patches or <a href="https://github.com/rsanheim/runcoderun-gem/issues">ideas</a> welcome!  This is very much in the spirit of "release early".  A command to tie in with <a href="https://www.aaronbedra.com/2009/06/05/getting-rcr-status-for-a-specific-project.html">the API</a> is clearly the next easy win for this.
