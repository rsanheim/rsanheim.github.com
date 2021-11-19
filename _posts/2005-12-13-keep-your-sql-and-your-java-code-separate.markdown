--- 
wordpress_id: 138
layout: post
title: Keep your sql and your java code separate
wordpress_url: https://www.robsanheim.com/?p=138
---
(assumption: using Spring JDBC or some other thin JDBC layer, obviously this does not apply to ORM)

At what point in the process do you decided to take all your sql out of your data access layer and put it into plain property files or sql files?  This gives you the <a href="https://www.c2.com/cgi/wiki?PowerOfPlainText">PowerOfPlainText</a> but adds an additional layer of indirection, and could also violate DRY where you could generate SQL programmatically if you kept more of it in the code.

This would also jive more with <a href="https://en.wikipedia.org/wiki/Separation_of_concerns">separation of concerns.</a>  If you add three fields to the where clause to better hit an index, you shouldn't have to touch your java code at all.  If you want to map things into new model objects, you shouldn't have to worry about the sql beyond "I have these five fields, put them somewhere".  

Right now I'm leaning towards having sql out in plain .sql files for everything but the smallest apps.  This gives you the power to run sql directly with whatever tool you want, and also lets you recreate schemas or test data very easily.  This is the route iBatis takes, and I haven't had a chance to use it in anger yet, but everything I've heard about it has been pretty good.

(kudos to <a href="https://www.jameshalberg.com">Jim</a> for letting me rant about this to him over IM)
