--- 
wordpress_id: 83
layout: post
title: JIA - Matt Raible - Comparing Java Web Frameworks
excerpt: review of Matt's presentation at Java in Action comparing JSF, Struts, Spring, Tapestry, and WebWork
wordpress_url: http://www.robsanheim.com/?p=83
---
I'm a little late coming with these session reviews, but I've been crazy busy getting caught up back at home.  Matt's session was three hours long and as he <a href="http://raibledesigns.com/page/rd?anchor=java_in_action_presentations_and">admitted</a>, should've probably been less time.  I think the overall presentation would've been great if it weren't for the technical problems.  

Matt is a natural presenter, using a very casual conversational tone and tried to keep things interactive in an environment that never didn't foster lots of interaction (note to TechTargert - we don't need mics! just let us ask our questions!).  The first half was good, though some of the slides were really hard to read from the back of the room.  Then he started the live coding, and it went downhill from there.  He did use personally created templates for all of his code, so a lot of the room for error was removed right there.  I will definitely be using that idea for future presentations.  Most of the problems seemed to be configuration or deployment based.  I still liked seeing a lot of code, though, and Matt did well considering the circumstances.  

As for the actual frameworks, he compared JSF, Struts, Spring, Tapestry and WebWork, and it seemed that WebWork came out on top.  JSF and Tapestry looked powerful but far too complex for the typical CRUD java web app, and Tapestry suffers from lack of adoption.  Everyone hates Struts (duh).  Spring MVC is a better alternative for a request based framework, but has a fairly high learning curve.  

<a href="http://www.opensymphony.com/webwork/">WebWork</a> looked very easy to me, and the actions you write are completely servlet independant, so you can test them without any mocking or container running.  The main complaint WebWork has had is lack of documentation, but <a href="http://www.amazon.com/exec/obidos/tg/detail/-/1932394532/qid=1128052468/sr=8-1/ref=pd_bbs_1/102-3725223-1212127?v=glance&s=books&n=507846"><i>WebWork in Action</i></a> just came out so it seems to be improving.  I also really like the fact that WebWork is resuing other open source components where it makes sense, like RIFE and DWR integration and <a href="http://blogs.opensymphony.com/webwork/2005/09/spring_and_webwork_together.html">using Spring for its IoC container.</a>  I'll have to take a look at WebWork once it reaches 2.2 final.  
