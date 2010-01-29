--- 
wordpress_id: 393
layout: post
title: Git Clone vs cp -R --> WTF?
wordpress_url: http://robsanheim.com/2008/07/30/git-clone-vs-cp-r-wtf/
---
I knew git was fast, and I even knew it was faster than a lot of plain linux local file operations.  Still, this still blew me away:

[code]rsanheim@ares:~/src/personal/oss $ du -hd 0 insoshi/
 26M	insoshi/

rsanheim@ares:~/src/personal/oss $ time git clone insoshi/ /tmp/insoshi
Initialize /tmp/insoshi/.git
Initialized empty Git repository in /private/tmp/insoshi/.git/
Checking out files: 100% (2193/2193), done.

real	0m3.826s
user	0m0.251s
sys	0m0.658s

rsanheim@ares:~/src/personal/oss $ time cp -R insoshi/ /tmp/insoshi_cp

real	0m9.065s
user	0m0.114s
sys	0m1.442s
[/code]
Ok, so a 26 meg repo takes almost three times as long to copy via a recursive cp than a local git clone.  Thats a fairly small repo, lets try something bigger:

[code]
rsanheim@ares:~/src/relevance $ du -hd 0 rails
 75M	rails

rsanheim@ares:~/src/relevance $ time git clone rails /tmp/rails2
Initialize /tmp/rails2/.git
Initialized empty Git repository in /private/tmp/rails2/.git/

real	0m2.321s
user	0m0.151s
sys	0m0.465s

rsanheim@ares:~/src/relevance $ time cp -R rails/ /tmp/rails

real	0m7.133s
user	0m0.067s
sys	0m1.505s
[/code]

The rails repo at 75 megs is still ~ 3 times faster.

Obviously, this is not scientific at all, but the point is pretty clear.  Git is doing some magic that lets it move files around locally 2 to 3 times faster than a plain copy.  From looking at the man page, I would guess it has something to do with git using hardlinks for things in .git/objects when cloning locally.  My linux fu falls down a bit here -- what are the ramifications of using hard links versus doing a "real" copy?

(This also makes me want to try out <a href="http://eigenclass.org/hiki/gibak-backup-system-introduction">gitbak</a> even more...)
