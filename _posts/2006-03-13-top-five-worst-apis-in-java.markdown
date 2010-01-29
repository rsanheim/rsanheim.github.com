--- 
wordpress_id: 209
layout: post
title: Top Five Worst APIs in Java
wordpress_url: http://www.robsanheim.com/?p=209
---
Its monday morning and I forgot my coffee thermos at home.  Drinking corporate coffee sucks.  Guess I might as well complain about Java.

<ul><li>Calendar - Bad.</li>
	<li>Date - Worse?  Date and Calendar might be the most ridiculous Java APIs ever created.  With date you can at least say getYear or getMonth, but then the results are the weird "year represented by the date, minus 1900".  With calendar you have the wonderful abstract get approach - ie myCal.get(Calendar.YEAR), myCal.get(RANDOM_MEANINGLESS_INT).  Would an immutable, easy to use date object be too much to ask for?  Couldn't Java 7 just incorporate <a href="http://joda-time.sourceforge.net/">JodaTime</a> or something?</li>

	<li>BigDecimal/BigInteger - Steve <a href="http://www.cabochon.com/~stevey/blog-rants/numbers-minilanguage.html">covers</a> this one must better then I can.  Even incredibly simple calculations become a horribly verbose mess with the BigNum objects.  One case where you really need operator overloading.</li>

	<li>ResultSet - why can't I just iterate over everything in my row?  Why can't I get a map of the values keyed by column header?</li>

	<li>Format, NumberFormat, DateFormat, etc. - <a href="http://java.sun.com/j2se/1.4.2/docs/api/java/text/SimpleDateFormat.html">SimpleDateFormat</a> really isn't, and these classes end up making the smallest task difficult in order to have ultimate flexibility.  Not a great trade off for most cases.</li>
</ul>
