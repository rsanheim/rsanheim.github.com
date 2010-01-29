--- 
wordpress_id: 168
layout: post
title: Naming test objects - mock, stub, fake?
excerpt: consistent names for "test doubles"
wordpress_url: http://www.robsanheim.com/?p=168
---
<a href="http://www.martinfowler.com">Martin Fowler</a> recently <a href="http://martinfowler.com/bliki/TestDouble.html">posted</a> about the confusion regarding what to name test doubles, and proposes a standard from Gerard Meszaros' <a href="http://www.amazon.com/exec/obidos/redirect?tag=panasonicyout-20%26link_code=xm2%26camp=2025%26creative=165953%26path=http://www.amazon.com/gp/redirect.html%253fASIN=0131495054%2526tag=panasonicyout-20%2526lcode=xm2%2526cID=2025%2526ccmID=165953%2526location=/o/ASIN/0131495054%25253FSubscriptionId=0EMV44A9A5YT1RVDGZ82">upcoming book</a>.  The names are as follows, with descriptions paraphrased from the <a href="http://tap.testautomationpatterns.com:8080/Using%20Test%20Doubles.html">using test double page</a> at the books outline:
<a href="http://www.amazon.com/exec/obidos/redirect?tag=panasonicyout-20%26link_code=xm2%26camp=2025%26creative=165953%26path=http://www.amazon.com/gp/redirect.html%253fASIN=0131495054%2526tag=panasonicyout-20%2526lcode=xm2%2526cID=2025%2526ccmID=165953%2526location=/o/ASIN/0131495054%25253FSubscriptionId=0EMV44A9A5YT1RVDGZ82" title="View product details at Amazon"><img class="right" src="http://images.amazon.com/images/P/0131495054.01._SCTHUMBZZZ_.jpg" alt="XUnit Test Patterns : Refactoring Test Code" /></a>
<ul>
<li>Dummy Object: placeholder object that is passed to the code under test as a parameter but never used</li>
<li>Test Stub is an object that is used by a test to replace a real component to force the system down the path we want for the test.  A stub may also record info about how it was called (ie <code>stub.wasMethodCalled()</code> or <code>stub.numberOfTimesMapResultSetCalled()</code></li>
<li>Mocks fake implementation by returning hard coded values or values preloaded - they can also verify that the correct calls were made in the right order</li>
<li>Fake objects replace the functionality of the of the real object with an alternate implementaiton, ie returning a canned list of values instead of hitting a database</li>
</ul>
I'm not sure if these names jive with what I am used to, but as long as the community can agree on some sort of consistent standard and stick with it I will happily adopt it.  Trying to explain the difference between an EasyMock provided mock and a canned "fake object" gets tiring.
