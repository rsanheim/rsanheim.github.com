---
layout: post
title: "Overvaluing Intelligence"
regenerate: true
---

I've been listening to Dwarkesh Patel's podcasts after hearing him interviewed on [EconTalk (a long time favorite of mine)](https://www.econtalk.org/the-past-and-future-of-ai-with-dwarkesh-patel/). For all his youthful naivety I admire his ability to have _real-talk_ across a broad range of things: [AI evangalism & predictions](https://www.dwarkesh.com/p/scott-daniel), deep dives into [WWII history](https://www.dwarkesh.com/p/sarah-paine), [notes on China](https://www.dwarkesh.com/p/notes-on-china-narration), [even more AI stuff (but more grounded?!)](https://www.dwarkesh.com/p/sholto-trenton-2) from two Anthropic engineers. 

A recent standout episode was with Tyler Cowen about [bottlenecks with AI](https://www.dwarkesh.com/p/tyler-cowen-4). Cowen brings up some key things that most of the standard AI crew don't really talk about, or if they do they gloss over it with a lot of hand-waving.

>[Patel: asks why AI won't lead to a huge increase of world economic productivity once we hit that mythical acceleartion sweet spot - i.e. why won't AI improve all parts of the economy like it is in software]

>I'm not sure I'm the one to diagnose, but I would say when I'm in the Bay Area, Like the people here, to me, are the smartest people I've ever met, on average. Most ambitious, dynamic, and smartest, like by a clear grand slam, compared to New York City or London or anywhere. That's awesome and I love it.

> But I think a side result of that is that people here overvalue intelligence and their models of the world are built on intelligence mattering much, much more than it really does. [...]

> But I just think if you could root that out of your minds, it would be pretty easy to glide into this expert consensus view that tech diffusion is universally pretty slow, and that's not going to change. No one's built a real model to show why it should change, other than just sort of hyperventilating blog posts about everything's going to change right away.

This is of course not a new criticism of tech culture. Tech bros gonna tech bro. Same as it ever was.

But it is especially important to bear it in mind during times of great hype and speculation like we are in now. 

I'm consistently amazed by Claude Code and Cursor and use them everyday. LLMs are insanely useful tools, once you learn how to use them well. But at the end of the day someone has to review, manage, prioritize, QA, ship, and support all that code your favorite LLM churns out...at least if you wanna get past v1.0 and have something live longer than a weekend.  You know what a lot of those other things involve? Humans, doing human things: talking to other people, going thru test plans, monitoring in production, responding to exception reports or following up on support issues. 

You can unleash Copilot or Claude on your Github Issues or Jira tickets, and it can probably handle simple things on its own, assuming you've got guardrails and good tooling. That is an amazing feat in of itself, and I think worth celebrating. Removing toil and moving clear, obvious refactoring/cleanup tasks from the backlog to `@claude handle the rename specified in #1234` is super helpful!

Those things are a far cry from building a new major feature without disrupting user experience or core workflows, or transitioning core models in your DB schema at scale without downtime and without corrupting data. Or, more importantly, figuring out and advocating for building the right things in an inherently costrained environment.

The more I think about "AI acceleration" within software development, the more it feels premature, even as I use LLMs more and more. Our industry hasn't figured out how to manage the code produced by frail, slow-thinking, context limited humans. How exactly will LLMs accelerate business _outside_ softare, where the context, tools, and training data are limited, foreign, and far less accessible compared to software dev?













