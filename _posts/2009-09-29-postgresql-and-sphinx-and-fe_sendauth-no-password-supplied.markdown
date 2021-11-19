--- 
wordpress_id: 442
layout: post
title: Postgresql and Sphinx and fe_sendauth no password supplied
wordpress_url: https://robsanheim.com/?p=442
---
Fun fact learned today about interactions between Postgresql and Sphinx.  Assuming you are using Postgres as your app's database, and you are wiring Postgres as the Sphinx data source, you *must* set a database level password for your database user.  You also cannot use the <a href="https://www.postgresql.org/docs/8.3/static/auth-methods.html">'trust'</a> mode in Postgres and try indexing without a password.  This can be especially confusing when you see that your Rails based db operations all work fine with no password, but then Sphinx indexing (via Thinking Sphinx, in  this case) fail with this error:

<code>fe_sendauth no password supplied</code>

If you decide to setup your postgres database user to have a null password (the default I believe if you don't specify one on creation), or you turn postgres auth mode to "trust", you can never index data with this user.  Sphinx <a href="https://sphinxsearch.com/forum/view.html?id=4355">_requires_</a> postgres users have actual passwords and use them for auth, even if postgres itself does not care.  Note that I'm referring to the database user password, *not* the OS level password.

Moral of the story: if you plan on using Sphinx and Postgres, make sure you have passwords wired for your Postgres user, even in dev/test environments.
