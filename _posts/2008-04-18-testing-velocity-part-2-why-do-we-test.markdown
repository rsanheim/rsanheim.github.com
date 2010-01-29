--- 
wordpress_id: 386
layout: post
title: Testing Velocity Part 2 - Why do we test?
wordpress_url: http://robsanheim.com/2008/04/18/testing-velocity-part-2-why-do-we-test/
---
A couple weeks ago, I <a href="http://robsanheim.com/2008/03/26/testing-velocity-keeping-your-test-suite-fast-part-1/">began a series</a> on keeping your test suite fast and effective.  I now am going to digress a bit, take a step back and view the big picture to establish context.

Before addressing test performance and what makes up a good test, we should ask ourselves why is it that we write tests at all?  If we want to be effective, we should always stay conscious of the overall goal of testing, as well as the specific goals behind each test in context.

Some would argue that tests are primarily a design tool.  Or that tests are a living, breathing, specification for our code.  Others would say it's primarily a means to drive and maintain quality.  Some may say that tests are useful to ensure that the really difficult parts of our system work, or to keep lax developers in line.

Testing is *only* valuable and useful insofar as it supports software as a cooperative game.  When you think "cooperative game", imagine rock-climbing, or ?  To quote Alistair Cockburn:

<cite><em>Software development is a (resource-limited) cooperative game of invention and communication. The primary goal of the game is to deliver useful, working software. The secondary goal, the residue of the game, is to set up for the next game. The next game may be to alter or replace the system or to create a neighboring system.</em></cite>

So is testing for design, or quality, or correctness, or communication?  The answer is that it's for *all* of those things (and more) as long as it helps deliver working software and prepare for the next game!  So when someone asks, "Why do you write tests?  Why do you care about the speed of your tests?"  The first answer is, "It depends."  It depends on the software you are delivering, on the teammates and domain you are working with, and on what the next game (if any) is.  Since every software project will be different, clearly how you write the code and its tests will differ.  An embedded system targeting your phone will have a much different test suite than a large enterprise web app.

This digression is to clarify debates I've heard (and been involved in) over issues like what should a "proper" unit test should do, how much setup is okay, mocks or stubs or fake objects, and when it's okay to mock/stub versus when it's not okay.  There are not hard and fast answers to any of these questions.  You need to consider context: What is being built?  What are the current technical issues?  Does the client want to run (or create) acceptance tests?  How slow is the test suite currently, and is it impacting dev speed?  How large is the system, and how much larger do you expect it to be?  Who will be maintaining the system after it's released, and what will their skill level be?  

Answer those types of questions before making statements like "this spec is doing too much setup and runs too slow," or "we shouldn't be stubbing in a functional test like this."  It will ensure that your discussions and debates will stay grounded and useful instead of becoming endless religious debates.  Keep context and the cooperative game model of software in the back of your mind, and I will too as I continue this series and try to lay out some practical, overall guidelines.
