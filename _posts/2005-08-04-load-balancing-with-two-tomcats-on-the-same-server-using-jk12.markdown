--- 
wordpress_id: 41
layout: post
title: Load balancing with two Tomcats on the same server using JK1.2
wordpress_url: https://www.robsanheim.com/?p=41
---
Article over at <a href="https://www.adcworks.com/blog">adc works blog</a> on load balancing with two instances of Tomcat on the same server.  The idea being you can move in production changes without totally bringing down your app, as you will always have one instance of it up.  Session replication is not taken into consideration with this approach.

<a href="https://www.adcworks.com/blog/index.php/archives/2005/08/03/load-balancing-with-tomcat-55-and-jk-12/">Load Balancing with Tomcat 5.5 and JK 1.2</a>.

Are there any other ways to maintain uptime while doing changes to production apps in tomcat?  Particularily without two instances (and assuming its more complicated then just a single class change, for instance...)

Technorati on tomcat: <a href="https://www.technorati.com/tag/tomcat" rel="tag">https://www.technorati.com/tag/tomcat</a>
