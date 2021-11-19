--- 
wordpress_id: 195
layout: post
title: Sql standards - how exactly did this get so f'ed up?
wordpress_url: https://www.robsanheim.com/?p=195
---
Lets say you want to get the first n number of rows from a result set, to do pagination or because you don't care about the rest of the rows or whatever.  You would think that there would be some relatively standard way defined in sql, and then the database vendors would all try to follow that.  It would be reasonable if vendors supported the standard <strong>and then</strong> provided their own super cool optimizied way.  

If you take a look at this <a href="https://troels.arvin.dk/db/rdbms/#select-limit">comparison page</a>, however, you'll see that only 2 of the 5 vendors listed support Rownumber(), and then each vendor seems to go out of their way to do it completely different.    Use "top n" in the select clause, "fetch first" after the order by, use "limit n".  Its not like you can just tweak a clause at the end of the statement to try and be compatibile, for some of the differences you have to rewrite the whole statement.  And this page only lists five vendors, I'm sure if you included some of the smaller vendors it would just get worse.

This is ridiculous.  This cannot be that difficult.  Why can't the vendors just say "lets work towards ANSI 200x for future versions, because the current situation sucks and we are screwing the users".  I understand they all want to push their own "optimized" features, but why not do that over a minimal baseline that is common amongst everyone?

As a side note, are there any official pages for what the ANSI SQL standard actually is?  Does ANSI SQL even <a href="https://builder.com.com/5100-6388-1046268.html">matter</a> anymore?  
