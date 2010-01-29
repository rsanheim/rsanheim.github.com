--- 
wordpress_id: 25
layout: post
title: Java technical interview guide - part 1
wordpress_url: http://www.robsanheim.com/?p=25
---
<b>update 8/31/05: I have written <a href="http://www.robsanheim.com/2005/08/31/java-technical-interview-questions-part-two-some-answers/">part two</a> with some possible answers.  Also, renamed the post.</b>

I did a technical evaluation for a candidate my employer was looking at awhile ago, so I had an opportunity to try and figure out a good set of technical questions for a prospective intermediate level Java web developer.  I'll just present a whole bunch of questions I came up with - no answers though.  I might start up an answers post at a later date, but I don't want to make this too easy for those trying to fool interviewers. =)  Obviously, if you ask every question I have listed here your interview could take hours, so pick and choose what you like.  I'd be interested in feedback for ideas on important topics I've overlooked or questions that are unfair or unnecessary.  I've tried to avoid things that can be easily answered with a quick google search, such as basic syntax and API method questions.

Anyways, on to the questions. <!--more-->

<h3>General Intro Questions</h3>
Just laying the ground work to help lead the way for areas to focus on...
<ul>
	<li>Give me a high level description of your experience with the Java platform.  What APIs do you have experience with?  Servlets?  J2EE?  Swing?</li>
        <li>What development methodologies have you used?  Which one have you liked the most?  The least?</li>
	<li>What open source frameworks do you have experience with?</li>
	<li>What other languages have you used?</li>
</ul>

<h3>Object Oriented Principles</h3>
<ul>
	<li><a href="http://c2.com/cgi/wiki?DefinitionsForOo">Define object oriented programming</a> (quite a loaded question...).  What are the key OO <a href="http://c2.com/cgi/wiki?PolymorphismEncapsulationInheritance">principles</a>?</li>
	<li>Describe polymorphism.</li>
        <li>Describe inheritance ("is-a") and composition ("has-a").  Can you give an example of a use case for each?</li>
	<li>What is coupling?  Why do we want loose coupling in our systems?</li>
</ul>

<h3>Java Basics</h3>
Some very fundamental questions I think any "non-beginner" level dev should know.  If there are a lot of problems with these it may not be worth continuing.
<ul>
	<li>What is the difference between abstract classes and interfaces?</li>
	<li>Explain the access modifiers in Java.</li>
	<li>Talk about method overriding and method overloading and their differences.</li>
	<li>Why does Java have exceptions?  What is the difference between checked and unchecked exceptions?</li>
	<li>What are constructors?  Are they inherited?</li>
	<li>What is the static modifier used for in regards to classes and methods?</li>
        <li>What are the <a href="http://java.sun.com/j2se/1.4/docs/api/java/lang/Object.html">equals() and hashcode()</a> ?  Describe their contracts.</li>
        <li>When do you use String and when do you use StringBuffer/StringBuilder</li>
</ul>

<h3>Java Intermediate/Advanced</h3>
<ul>
<li>Explain the following statement: Java is <strong>always</strong> <a href="http://www.javaranch.com/campfire/StoryCups.jsp">pass-by-value.</a></li>
	<li>How do you create an immutable type?  What are the advantages of immutability?</li>
	<li>What is a static inner class?  Can you provide an <a href="http://java.sun.com/j2se/1.4.2/docs/api/java/util/Map.Entry.html">example </a>from the Java API?</li>
	<li>What are the implications of implementing serializable in an object?</li>
	<li>Why would you declare a private constructor?</li>
        <li>When do you want to use unchecked exceptions and when do you want to use checked?</li>
        <li>Can you explain <a href="http://www.cs.technion.ac.il/~genadyb/strings/strings.html">how Strings</a> are "<a href="http://mindprod.com/jgloss/interned.html">interned</a>" in Java?</li>
	<li>What are enumerated types?  Why would you use them?</li>
</ul>

<h3><a href="http://java.sun.com/j2se/1.4.2/docs/guide/collections/">Java Collections</a></h3>
<ul>
	<li>What are the core interfaces of the Collection framework?</li>
	<li>How do Vector and HashTable relate to Collections?</li>
	<li>Desribe typical use cases or examples of common uses for Map, Set, and Lists.</li>
	<li>What method(s) should override for objects you plan to add to sets or maps?</li>
        <li>How do you get an immutable collection?</li>
</ul>

<h3>
</h3><h3>Threading</h3>
If a developer works only in the heavily abstracted world of Spring/Hibernate/whatever, they may not have had to touch an actual Runnable since college.  Still, its good to know about threading at least on a basic level.
<ul>
	<li>What does the synchronized key word do?  Where is it valid to use it (ie inside a method call, static block, etc)?</li>
        <li>Explain the two ways to instantiate threads in Java.</li>
	<li>What is "<a href="http://www.cs.umd.edu/~pugh/java/memoryModel/DoubleCheckedLocking.html">double-checked locking</a>"?  What <a href="http://www-106.ibm.com/developerworks/java/library/j-dcl.html">design pattern</a> is it typically associated with?  What is wrong with it?</li>
        <li>What is a daemon thread?  How do you create one?</li>
        <li>What method do you use to start a thread?</li>
 </ul>

<h3><a href="http://www.amazon.com/exec/obidos/tg/detail/-/0596005407?v=glance">Servlets and JSPs</a></h3>
<ul>
	<li>What are the steps to create a basic servlet?</li>
	<li>Describe the lifecycle of a basic servlet - for instance, when are they created?  What method is called from a typical HTTP request?  What about requests and threads?</li>
	<li>What does it mean to say that HTTP is stateless?  How do servlets provide a possible solution to maintain state for web applications?</li>
	<li>Are JSP's <a href="http://www.jguru.com/faq/view.jsp?EID=368">thread safe</a>?</li>
	<li>What are Listeners?  What is a typical use for a StartupListener?</li>
	<li>What are <a href="http://java.sun.com/products/servlet/Filters.html">filters </a>and why would you use them?</li>
         <li>Describe the four different scopes available with servlets?
</li></ul>

<h3><a href="http://c2.com/cgi/wiki?DesignPatterns">Design Patterns</a></h3>
<ul>
	<li>What are the three types of design patterns?</li>
        <li>Can you talk about the <a href="http://gee.cs.oswego.edu/dl/ca/ca/ca.html">history</a> of design patterns?</li>
	<li>Why use design patterns?</li>
         <li>What is the role of composition (aggregation) in design patterns?</li>
	<li>What design patterns do you use often and have the most experience with?  Can you talk about a typical use case?</li>
        <li>Can you provide a description of any of the following patterns?  Strategy, State, or Template method?</li>
         <li>What is <a href="http://c2.com/cgi/wiki?ModelViewController">Model View Controller</a>, and why would you want to use it?  What are some of the disadvantages of it?
	</li><li>What is <a href="http://www.theserverside.com/articles/article.tss?l=IOCBeginners">inversion of control</a>, and <a href="http://www.martinfowler.com/articles/injection.html">what does it give you?</a></li>
</ul>

<h3>Open Ended Questions</h3>
These questions are more to just stir discussion and debate and to get a feel for the candidate, rather then to get the "right" answer.
<ul>
	<li><a href="http://c2.com/cgi/wiki?DesignChallengesForInterview">How would you build a software version of Monopoly?</a></li>
        <li>Can you <a href="http://www.jvoegele.com/software/langcomp.html">compare </a>(insert dynamic language of choice here - Ruby/Python/Lisp/etc) to Java?  When would you prefer one over the other?</li>
        <li>What do you think is the most <a href="http://en.wikipedia.org/wiki/The_Mythical_Man-Month">common cause of project failure</a> in the software development business?</li>
        <li>What do you think of the rise of open source over the last ten years?  Where do you see open source in the future?</li>
<li>What does <a href="http://agilemanifesto.org/">agile development</a> mean to you?</li>
	<li>What is your ideal development environment like?  Both in terms of hardware and software, and location and surroundings?</li>
	<li>What was the last technical book you read?  Give me the Cliff Notes version of it.</li>
	<li>What are some of your favorite resources beyond Google?  This could include websites, magazines, technical authors, experts, favorite blogs, etc.</li>
	<li>Do you have experience with Test Driven Development?  If so, what do you think of it?</li>
<li>What will be the next language or development topic you want to learn about?</li>
</ul>
