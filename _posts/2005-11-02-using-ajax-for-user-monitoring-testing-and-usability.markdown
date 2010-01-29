--- 
wordpress_id: 101
layout: post
title: Using ajax for user monitoring, testing, and usability
wordpress_url: http://www.robsanheim.com/?p=101
---
I'm liking Eric's <a href="http://radio.javaranch.com/pascarello/2005/11/01/1130878004388.html">idea</a> on using Ajax for monitoring user actions for automatic error logging/capturing.  Basically he is turning the tables on the common misconception that ajax can be used for evil "user spying" by instead using ajax to log all the users actions throughout the page for testing.  He'll be able to go through the logs and recreate exactly where defects happen according to the timestamp of events.  This could hopefully remove the dreaded user complaint of "I don't remember what I was doing, the app just crashed on me".

I can see even greater potential for this type of thing as a poor-man's <a href="http://en.wikipedia.org/wiki/Usability_lab">usability lab</a>.  If you can playback the users interaction with the page, you can watch exactly where and what they are clicking on and where your app works and where it doesn't.  

Maybe record your user thinking out loud while they are doing this, and then playback the audio while you watch the capture for more insights.  Though if you are going that far I'm not how much value you get over the standard capture program + camcorder setup, but maybe for remote usability for instance.
