---
layout: post
title: "Day 2 Craftsmanship Swap at 8th Light"
---

(note: this was from my stint on Wednesday, July 7th at 8th Light)

For Day 2 of my stint at 8th Light, [Skim](https://twitter.com/skim "") and I came in early enough to find a relatively empty office.  I paired with Skim on an app he has been building as part of his apprenticeship at 8th Light.  All apprenticeships have to complete several projects during there time, with their mentor (a craftsman at 8th Light) acting as the product owner.

Steve's application is a Tic-Tac-Toe game built in Ruby, which had the additional twist of having both a console UI and a [Limelight](https://limelight.8thlight.com/main/sparkle) UI.  Limelight is a UI framework built in JRuby by the 8th Light guys, and I can definitely see myself reaching for it the next time I need to built a cross-platform rich UI.

I helped Steve out with some Rspec issues and also increased his git-fu, and we discussed some of the difficulties in testing threading.  A `Thread.new` call in his game was causing timing related failures, and we tried to extract out the threading implementation enough to allow his specs to work around it.

Lunch was taken out of the office at [Thai Gourmet](https://www.yelp.com/biz/thai-gourmet-libertyville), which was delicious.  It was at least on par with Thai Cafe, which is a favorite at Relevance.

I had to fight off curry drowsiness post-lunch to pair with Doug on the same application we had paired on in [day 1]("https://robsanheim.com/2010/07/08/day-1-craftsmanship-swap-at-8th-light/").  The application uses [DRb](https://ruby-doc.org/core/classes/DRb.html) and [DRbFire](https://drbfire.rubyforge.org/classes/DRbFire.html) under the hood to manage client-server communication.  Based on some issues reported from client installations we suspected some socket or connection related issues in the DRb related part of the codes.  And so began a deep dive into DRbFire and DRb itself.

DRbFire is actually a protocol on to of DRb that does a neat little trick to allow DRb to connect across networks, such as when a client and server need to talk through firewalls or a NAT.  Given the fact that 99% of clients will jump through a NAT or firewall at some point, what DRbfire does is pretty cool.

Doug and I dusted off a simulator that 8th Light has written to fake out multiple clients connecting to the server without having a ton of real machines around.  By the end of the day we had discovered that something strange was definitely going on, as simulating 40+ clients connecting to the server and disconnecting resulted in over 80 socket connections hanging around in a [CLOSE_WAIT](https://blogs.technet.com/b/janelewis/archive/2010/03/09/explaining-close-wait.aspx) state on the server.  We were able to reproduce the same error that had been reported from client installations, but weren't 100% sure of the exact source yet.

Dinner that night was at a Hibachi-style steakhouse with Skim, Micah, and his family.  The Japanese knife dude managed to impress without any injuries, and fine flame broiled food was had by all.  I was back to the hotel by 8 or so and I turned in for an early night.  Apparenlty the travel and pairing was finally catching up to me.