--- 
wordpress_id: 252
layout: post
title: "Comand Line Tip: How to List Only Directories"
wordpress_url: https://www.robsanheim.com/?p=252
---
Finding this took over three tries with Google, which means it took too long and that I'll forget as soon as I need to do it again.

To list only directories in the current directory, this does the trick:

<code>ls -d */</code>

Though it doesn't make since to me, because the -d option for ls says:

<blockquote>-d      Directories are listed as plain files (not searched recursively).</blockquote>

And "ls -d" alone doesn't do anything for me...but whatever.

There are some other ways discussed <a href="https://ubuntu.wordpress.com/2005/10/19/list-only-the-directories/">here at the Ubuntu log</a>.
