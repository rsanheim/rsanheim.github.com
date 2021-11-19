---
layout: post
title: "New Releases: LogBuddy 0.5 and CapGun 0.2.4"
---
Hey now, it has been quiet here for too long, so what better way to bring some life back then open source updates?

First, [LogBuddy](https://github.com/relevance/log_buddy), the little developer tool that could, has been updated to 0.5.  What is LogBuddy?  LogBuddy is a very small tool that logs the name of the thing your are logging, plus its value.  Stop typing `puts my_var => #{my_var}` while doing ad-hoc debugging.  For example, assuming you have a local, an ivar, and a class var called 'a':

    d { a }       => a = "foo"
    d { @a }      => @a = "my var"
    d { @@bar }   => @@bar = "class var!"

There are a few significant changes in this release.  

* You no longer have to call `LogBuddy.init` in order to have the `d` method available everywhere - now it just happens upon require unless you specifically set `SAFE_LOG_BUDDY` in your environment.  This makes LogBuddy easier to require and use for small tasks.

* No more `logger` method mixed in everywhere - that was a bad idea and just asking for namespace bugs.

* LogBuddy will no longer raise if the logged line of code is removed before the output is generated.  This probably only happened if you were coding quickly and using a tool like autotest or watchr to run tests on change.

[CapGun](https://github.com/relevance/cap_gun) adds deployment notifications to Capistrano, so you can email blast interested parties on deployments.  Version 0.2.4 fixes a bug where notifications would fail on the very first deploy due to a missing REVISION directory.  This version also got fixes for Rails 3 using the new ActiveSupport, thanks to [Jared Pace](http://twitter.com/jdpace) for those.