--- 
wordpress_id: 303
layout: post
title: My Command line toolkit for Ruby and Linux
wordpress_url: https://www.robsanheim.com/?p=303
---
Some common aliases and functions that I use, spread across various bash_login and .sh scripts.  This excludes a bunch of things that are specific to SeekingAlpha, of course.  A lot of this was cobbled together from similar lists and previous coworkers.

[code]
# general shortcuts
alias mv='mv -i'
alias cp='cp -i'
alias rm='rm -i'
alias :='cd ..'
alias ::='cd ../..'
alias :::='cd ../../..'

# listing files - I usually end up using 'l' since its quick and easy
alias l='ls -al'
alias lt='ll -t'
alias la='lt -a'
alias lth='ll -t|head'
alias lh='ls -Shl | less'

# apache
alias htreload='/etc/init.d/httpd reload'
alias htstart='/etc/init.d/httpd start'
alias htstop='/etc/init.d/httpd stop'
alias htlogs='cd /var/log/httpd'

# system monitoring
alias apache_process='ps -ef | grep httpd | grep -v grep | wc -l' # count apache processes
alias topcpu='ps aux | sort -n +2 | tail -10'  # top 10 cpu processes
alias topmem='ps aux | sort -n +3 | tail -10'  # top 10 memory processes

# systat rocks - https://perso.orange.fr/sebastien.godard/index.html
alias sar2='sar -u 2 0'
alias sar5='sar -u 5 0'

# a nice and easy process searcher - should work in mac osx and linux
# heading doesnt work -- need more grep trickery to grab any matches *and* the heading
if [ `uname` = "Darwin" ]; then
	function psg { 
		ps aux  | grep -i $1  | grep -v grep
	}
else
	function psg { 
		ps aux --heading | grep -i $1 | grep -v grep
	}
fi

# Ruby/Rails specific
alias gems='cd /usr/local/lib/ruby/gems/1.8/gems/'
alias sc='script/console'
alias ss='script/server'
alias rt='rake --trace | redgreen' # Rake Test (w/ color)
[/code]
