--- 
wordpress_id: 207
layout: post
title: java.awt.List - the Bane of IDE AutoCompletion
wordpress_url: https://www.robsanheim.com/?p=207
---
When I'm cruising in Eclipse, nothing disrupts flow like having to fix stupid import problems.  FOr example, I type in a reference to List and try to autocorrect it:

<img src='/wp-content/java_awt_list.png' alt='autocompleting List' />

Oh!  I wanted the standard collection type, not the AWT specific list!  Here, Eclipse, let me tell you I need the the standard list type another five million times while I autocomplete my 56th for loop over a collection.

But I'm not bitter.

Is there some way to fix this, short of hacking my JDK to remove AWT, since I never use it?  This is almost as bad as java.math.BigDecimal and com.ibm.math.BigDecimal when working under WSAD.

