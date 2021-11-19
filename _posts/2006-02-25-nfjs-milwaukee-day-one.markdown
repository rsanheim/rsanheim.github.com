--- 
wordpress_id: 201
layout: post
title: NFJS Milwaukee - Day One
wordpress_url: https://www.robsanheim.com/?p=201
---
The <a href="https://www.nofluffjuststuff.com/">No Fluff Just Stuff</a> tour kicked off today.  I made it down to Milwaukee in time, despite a frantic search for my keys that ended with finding them in my wife's jacket (of course).  After the registration and intro from Jay, I went over to see <a href="https://www.nofluffjuststuff.com/speaker_view.jsp?speakerId=6">Stuart's</a> talk on <a href="https://www.nofluffjuststuff.com/speaker_topic_view.jsp?topicId=257">Spring Dependancy Injection.</a>  

I know and use Spring day to day, but I figured it wouldn't hurt to go over the basics and I was curious to see what kind of presenter Stuart was.  It turned out to be a very good introduction to Spring, with a very clear explanation for why loose coupling and DI is a good thing.  His examples were clear and simple, with a nice balance of slides/diagrams and live code.  He also covered how J2EE already provides DI using the lookup model, and yet how that doesn't go as far as Spring as you are still tied to the container.  Of course, EJB3 and things like JBoss's <a href="https://docs.jboss.org/ejb3/embedded/embedded.html">embeddable container</a> have changed that to some extent, but in the end the more tests I can run w/o any container depedancy, the better.  I liked the fact that Stuart gave advice about what things to avoid in Spring (like autowiring and lifecycle methods), but I would've liked to see some discussion of <a href="https://martinfowler.com/bliki/ConstructorInitialization.html">constructor</a> vs <a href="https://martinfowler.com/bliki/SetterInitialization.html">setter</a> injection.

Stuart was using a ajax presentation tool called <a href="https://www.codecite.com/">CodeCite</a> (site is down as I write this) which looked pretty cool.  It handled sucking in the code into the html for the presentation automatically, so you don't end up copying code into the presentation everytime you change something.  Its an open source thing he's develped so it should be available once the site is back up.

After that session, I headed up to my room as I was feeling a bit out of sorts and wanted a nap.  Most of the afternoon sessions were things I saw last year, so I wasn't too worried about missing things.  

I did make it down for Dave Thomas' keynote "<a href="https://www.nofluffjuststuff.com/speaker_topic_view.jsp?topicId=325">Cargo Cults and Angry Monkeys</a>".  If you attend a NFJS, you really can't miss his keynotes, as they are fantastic.  

This year's was all about questioning conventional wisdom, and the fallacy of "if it ain't broke don't fix it".  He went after the sacred cows of object oriented development, design patterns, and type safety, among others.  He got in some great shots at Java in the progress, of course.  I won't go into the analogy of <a href="https://en.wikipedia.org/wiki/Cargo_cult">cargo cults</a>, as the wikipedia link covers it pretty well as does <a href="https://en.wikipedia.org/wiki/Cargo_cult_programming">the page</a> on cargo cult programming.  

The "angry monkeys" referred to an interesting primate experiement that I wish he had referenced or at least given some more background on.  The take-away I got from the talk was to think about why things are done a certain way, and <a href="https://www.robsanheim.com/2006/02/10/why-ruby/">question</a> <a href="https://discuss.joelonsoftware.com/default.asp?joel.3.309321.3">instead</a> of following the <a href="https://www.artima.com/weblogs/viewpost.jsp?thread=141312">herd</a>.  Something I'm sure most everyone could stand to do a bit more of.
