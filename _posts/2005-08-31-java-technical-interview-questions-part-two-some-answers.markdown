--- 
wordpress_id: 62
layout: post
title: "Java technical interview guide: part two - some answers"
wordpress_url: https://www.robsanheim.com/?p=62
---
In July I posted a <a href="https://www.robsanheim.com/2005/07/22/java-technical-interview-questions/">set of questions</a> for a Java technical evaluation based on an eval I did for my employer.  This is part two where I add some answers to those questions.  

Interviewers: many of these questions are very open ended and this post only lists one of many right answers.  This is only a starting point for conducting a decent Java interview, its no replacement for face to face time, live coding, etc.

Developers/interviewees: if you are relying soley on this post and others like it on to get through interviews or, heaven forbid, to get a job, you are only hurting yourself in the long run. =)
<!--more-->

<h3>Object Oriented Principles</h3>
<ul>
	<li><a href="https://c2.com/cgi/wiki?DefinitionsForOo">Define object oriented programming</a> (quite a loaded question...).  What are the key OO <a href="https://c2.com/cgi/wiki?PolymorphismEncapsulationInheritance">principles</a>?<p>
A fairly standard definition is the idea of breaking up a program into abstract objects.  An object is a unit capable of receiving and sending messages.  The three typical OO attributes are polymorphism, encapsulation, and inheritance, though not all OO languages have inheritance.  </p></li>
	<li>Describe polymorphism.
<p>Poly = many, morph = form, ie "many forms".  Polymorphism allows objects to take on different behavior depending on the runtime type, which the client need not be aware of.  A typical concrete Java example is where you have an <code>interface Shape</code> defined, with a <code>area</code> method.  Any concrete types that implement shape can return their area using their own algorithm, which clients do not have to be aware of.</p></li>


	<li>What is coupling?  Why do we want loose coupling in our systems?</li>
</ul>

<h3>Java Basics</h3>
Some very fundamental questions I think any "non-beginner" level dev should know.  If there are a lot of problems with these it may not be worth continuing.
<ul>
	<li>What is the difference between abstract classes and interfaces?
<p>An abstract class defines the contract and optionally default implementation for its methods - an interface only defines the contract (ie method signatures) - no implementation.  Abstract classes can have public or protected members, an interface can only have public members..</p></li>

	<li>Explain the access modifiers in Java.
<p>Access modifier specify where a method or attribute can be used.  Public - accessible from anywhere/anything.  Protected - accessible from the type where its defined or any subclasses.  Package - accessible from the class or subclass, but only within the same package.  Private - only accessible from within the class.</p></li>

	<li>Talk about method overriding and method overloading and their differences.
<p>A method is overrode when you define a method with the same signature as an accessible method in a superclass.  Method overloading is actually creating an entirely unrelated method with a different signature.</p></li>

	<li>Why does Java have exceptions?  What is the difference between checked and unchecked exceptions?
<p>Exceptions handle unexpected conditions.  If an exception is checked, it must be declared as part of the method signature using <code>throws</code> or it must be handled using <code>try...catch.</code>  Checked exceptions are typically for things that can be recovered from, such as a database record lock or bad user input.  Unchecked exceptions do not have to be explicitly handled by the programmer, and are for things that cannot be recovered from, such as programmer error or out of memory errors.</p></li>

	<li>What are constructors?  Are they inherited?
<p>Constructors are special methods used to create objects.  They are not inherited, but superclass constructors can be called using the <code>super</code> keyword.  If <code>super</code> is called it must be the first line in a constructor.</p></li>

	<li>What is the static modifier used for in regards to classes and methods?
<p>A static method is available on the class and is not associated with any specific instance.  Since a static method is at the class level, it cannot access instance data and can called without creating any instances of the class.</p></li>

        <li>What are the <a href="https://java.sun.com/j2se/1.4/docs/api/java/lang/Object.html">equals() and hashcode()</a> ?  Describe their contracts.
<p>Refer to <a href="https://www.amazon.com/exec/obidos/redirect?tag=manalangcom-20%26link_code=xm2%26camp=2025%26creative=165953%26path=https://www.amazon.com/gp/redirect.html%253fASIN=0201310058%2526tag=manalangcom-20%2526lcode=xm2%2526cID=2025%2526ccmID=165953%2526location=/o/ASIN/0201310058%25253FSubscriptionId=0EMV44A9A5YT1RVDGZ82" title="View product details at Amazon">Effective Java <img class="right" src="https://images.amazon.com/images/P/0201310058.01._SCTHUMBZZZ_.jpg" alt="Effective Java Programming Language Guide" /></a>, Bloch is the man on this type of thing.</p></li>

        <li>When do you use String and when do you use StringBuffer/StringBuilder
<p>To over generalize, use StringBuffer/Builder where you want to construct or process a String in some sort of expensive process, such as a long-running loop.  Use Strings for any other case.</p></li>
</ul>

<h3>Java Intermediate/Advanced</h3>
<ul>
<li>Explain the following statement: Java is <strong>always</strong> <a href="https://www.javaranch.com/campfire/StoryCups.jsp">pass-by-value.</a>

<p>When assigning an object to a variable, you are actually assigning the memory address of that object to the variable, therefore allowing calls to the variable to interact with the actual object.  So the value being passed is actually the memory location of the object, but to the programmer it looks as if you are passing around references to the object.  This results in object aliasing, meaning you can have many variables referring to the same object on the heap. </p></li>

	<li>How do you create an immutable type?  What are the advantages of immutability?
<p>Immutability means an object cannot be modified after it has been initialized.  This has many benefits for simplifying your objects and your program in general, since immutable objects are always in a valid state.</p></li>
	<li>What is a static inner class?  Can you provide an <a href="https://java.sun.com/j2se/1.4.2/docs/api/java/util/Map.Entry.html">example </a>from the Java API?
<p>A static inner class is a class tightly associated with its enclosing class but not tied to any specific instance.  Static inner classes can be instantiated independent of the enclosing class like any top level class.  A common example is the Map.Entry class, which provides the standard contract for accessing maps in the Collections api.</p></li>

	<li>What are the implications of implementing serializable in an object?
<p>A serializable object can be converted to a byte stream and stored on disk, allowing such things as session replication or storage in a database.  When you implement serializable, you must take into account the fact that changes to the object's members in the future may break compatibility with old versions.</p></li>

	<li>Why would you declare a private constructor?
<p>To control creation of an object, as an object with a private constructor cannot be instantiated outside of the instance.  A typical use case in with singletons.</p></li>
        <li>Can you explain <a href="https://www.cs.technion.ac.il/~genadyb/strings/strings.html">how Strings</a> are "<a href="https://mindprod.com/jgloss/interned.html">interned</a>" in Java?
<p>Strings are created once and stored ("interned") for later use, so <code>String blah = "foo";</code> and <code>String blah2 = "foo"</code> point to the same object.  This can be done because Strings are immutable.  The exception is where a <code>new String</code> is explicitly created.</p></li>
</ul>

More later as time permits...as always, comments and corrections are greatly appreciated.
