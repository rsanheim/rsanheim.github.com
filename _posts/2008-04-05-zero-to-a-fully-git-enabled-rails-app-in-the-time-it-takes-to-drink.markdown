--- 
wordpress_id: 382
layout: post
title: Zero to a Fully Git Enabled Rails App in the time it takes to drink an espresso
wordpress_url: http://robsanheim.com/2008/04/05/zero-to-a-fully-git-enabled-rails-app-in-the-time-it-takes-to-drink/
---
<strong>updated: </strong> now uses the real Rails git master at github, now that its live.

So you want to set up a fresh Rails app in a fresh git repo, with proper ignores setup, with vendor/rails using a git submodule (which enables switching to <strong>any</strong> Rails branch or tag locally)?   This isn't rocket science or anything, but I figured I'd post it to see what things could be done better.

<h4>Assumptions</h4>
<ul>
	<li>You have a working, recent version of git installed.</li>
	<li>You have the <a href="http://blog.nanorails.com/git-rails">git-rails</a> gem installed.</li>
	<li>You have the bash <a href="#aliases">aliases</a> at the bottom of the post.</li>
</ul>

<code>
rails app_name
cd app_name

git-rails init

gca -m 'initial commit'

git submodule add git://github.com/rails/rails.git vendor/rails
# bring in rails from github
git submodule init
# Submodule 'vendor/rails' (git://github.com/rails/rails.git) registered for path 'vendor/rails'

git submodule update

gca -m 'bring in rails via submodule'
# Created commit 3b67dee: bring in rails via submodule
#  2 files changed, 4 insertions(+), 0 deletions(-)
#  create mode 100644 .gitmodules
#  create mode 160000 vendor/rails

cd vendor/rails
gba # pick branch of Rails you wanna use
git co BRANCH # where BRANCH is the specific branch you want, unless you want the default of going against edge
</code>

You're done!

<span id="aliases">Here's those aliases you need:</span>

<code>
alias g='git'
alias gb='git branch'
alias gba='git branch -a'
alias gc='git commit -v'
alias gca='git commit -v -a'
alias gd='git diff | mate'
alias gl='git pull'
alias gp='git push'
</code>
