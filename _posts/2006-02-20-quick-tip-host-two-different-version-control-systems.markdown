--- 
wordpress_id: 196
layout: post
title: "Quick Tip: Host Two Different Version Control Systems"
wordpress_url: https://www.robsanheim.com/?p=196
---
I recently set up subversion to complement my cvs repository for version control.  I ported all my personal apps over, but one nice benefit I didn't anticipate was the ability to keep client projects or open source projects in my own repository at the same time.

For instance, I had a project for a client that I wanted to work on this last weekend from home.  The problem was the codebase was under cvs control at the client's pc, with cvs metadata locked to their repository.  Their cvs server is not accessible outside the client site.  Now if I really wanted to get that into my cvs repository, I could copy the whole project and rip out all the cvs metadata, then handle merging changes back into the connected project by hand.  But that sucks.  

Now that I have my own subversion server setup, all I had to do was "disconnect from repository" on the project in Eclipse and then share it with my svn server.  All the cvs metadata is saved, so when I'm done doing my work from home I sync everything up from my svn, disconnect from svn and reconnect to the clients cvs, and I'm ready to merge my latest changes.  No messing with metadata or copying things manually.

So its nothing groundbreaking, but it was a nice easy solution for sharing a project that is already under third-party cvs or svn control that you want into your repository as well.

