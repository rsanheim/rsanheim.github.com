---
layout: post
title: "Day 2 Craftsmanship Swap at 8th Light"
---

For Day 2 of my stint at 8th Light, [Skim](http://twitter.com/skim "") and I came in early enough to find a relatively empty office.  After clearing some outstanding email, I paired with Skim on an app he has been building as part of his apprenticeship at 8th Light.  All apprenticeships have to complete several projects during there time, with their mentor (a craftsman at 8th Light) acting as the stakeholder and client.

Steve's application was a Tic-Tac-Toe game built in Ruby, which had the additional twist of having both a console UI and a [Limelight](http://TODO) UI.  Limelight is a UI framework built in JRuby by the 8th Light guys, and I can definitely see myself reaching for it the next time I need to built a cross-platform rich UI.

I helped Steve out with some Rspec issues, and we discussed some of the difficulties in testing threading.  A `Thread.new` call in his game was causing random timing related failures, and we tried to extract out the threading implementation enough to allow his specs to work around it.

Lunch was taken out of the office at [Thai Gourment](http://TODO), which was delicious.  It was at least on par with Thai Cafe, which is a favorite at Relevance.

I had to fight off a curry infused drowsiness post-lunch to pair with Doug on the same application we had paired on in [day 1]("/2010-07-08-day-1-craftsmanship-swap-at-8th-light").  The application uses DRb and DRbFire under the hood to manage client-server communication.  Based on some issues reported from client installations we suspected some socket or connection related issues in the DRb related part of the codes.  And so began a deep dive into DRbFire and some of the DRb code itself.


* uses skype for all its standup calls
* awesome customer support / communication with QA team
  * customer writing acceptance tests -- yay!
* began deep drive into DRb w/ Doug
* paired with Skim in the morning
* lunch at delicious Thai Gourmet 
* dinner with Micah + family and Skim