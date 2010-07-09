---
layout: post
title: "Day 2 Craftsmanship Swap at 8th Light"
---

For Day 2 of my stint at 8th Light, [Skim](http://twitter.com/skim "") and I came in early enough to find a relatively empty office.  After clearing some outstanding email, I paired with Skim on an app he has been building as part of his apprenticeship at 8th Light.  All apprenticeships have to complete several projects during there time, with their mentor (a craftsman at 8th Light) acting as the stakeholder and client.

Steve's application was a Tic-Tac-Toe game built in Ruby, which had the additional twist of having both a console UI and a [Limelight](http://TODO) UI.  Limelight is a UI framework built in JRuby by the 8th Light guys, and I can definitely see myself reaching for it the next time I need to built a cross-platform rich UI.

I helped Steve out with some Rspec issues and also increased his git-fu, and we discussed some of the difficulties in testing threading.  A `Thread.new` call in his game was causing random timing related failures, and we tried to extract out the threading implementation enough to allow his specs to work around it.

Lunch was taken out of the office at [Thai Gourmet](http://TODO), which was delicious.  It was at least on par with Thai Cafe, which is a favorite at Relevance.

I had to fight off a curry infused drowsiness post-lunch to pair with Doug on the same application we had paired on in [day 1]("http://robsanheim.com/2010/07/08/day-1-craftsmanship-swap-at-8th-light/").  The application uses [DRb](http://TODO) and [DRbFire](http://TODO) under the hood to manage client-server communication.  Based on some issues reported from client installations we suspected some socket or connection related issues in the DRb related part of the codes.  And so began a deep dive into DRbFire and some of the DRb code itself.

DRbFire is actually a protocol on to of DRb that does a neat little trick to allow DRb to connect across networks, such as when a server has to go through a NAT to get to it's clients.  Given the fact that most net-connected PCs will jump through a NAT or firewall at some point, what DRbfire offers seems pretty essential.

Doug and I dusted off a simulator that 8th Light has written to fake out multiple clients connecting to the timeshare server without having to have many actual machines around.  By the end of the day we had discovered that something strange was definitely going on, as simulating 40+ clients connecting to the server and disconnecting resulted in over 80 socket connections hanging around in a CLOSE_WAIT state on the server.  We also were able to reproduce the same error that had been reported from client installations, but didn't weren't entirely sure of the exact source yet.

Dinner that night was at a Hibachi-style steakhouse with Skim, Micah, and his family.  The Japanese knife guy managed to impress without any getting harmed, and fine flame broiled food was had by all.  I ended up passing out early in the hotel room and skipping a planned run, but apparently I needed the sleep due to the stress of travel and the long days pairing.