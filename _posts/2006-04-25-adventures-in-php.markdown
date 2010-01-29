--- 
wordpress_id: 225
layout: post
title: Adventures in PHP
wordpress_url: http://www.robsanheim.com/?p=225
---
Been doing a lot of PHP in anger the past two weeks.  Its not the cleanest language, but you can definitely get stuff done quickly with it.  I've been getting used to the Wordpress source, and lots of plugins and hacks built on top of it.  Its pretty much at the oppositie extreme from the typical Java apps you see - a lot of simple, straightforward code, plenty of duplication, without a whole lot of thought given to abstractions or MVC.    The lack of any namespacing at all means a lot of dumb function names like mycompany_find_foo and what not.  The main docs at php.net are decent, but I wish they had a bit more structure enforced from something like javadoc.

The lack of any consistency for across the libraries is well known and been <a href="http://en.wikipedia.org/wiki/PHP#Criticism">written</a> <a href="http://www.zend.com/forums/index.php?t=msg&goto=1926&S=78078fe87a6294d51ddeb793fc461ce5">about</a> by <a href="http://www.sitepoint.com/blogs/2004/09/13/the-standard-php-library-worse-gets-better/">many</a>.  Then you have some great functions like these two:

<ul><li><a href="http://us3.php.net/strpos">strpos</a> - Returns the numeric position of the first occurrence of needle in the haystack string. Unlike the strrpos() before PHP 5, this function can take a full string as the needle parameter and the entire string will be used.</li>

<li><a href="http://us3.php.net/manual/en/function.strrpos.php">strrpos</a> - Returns the numeric position of the last occurrence of needle in the haystack string. Note that the needle in this case can only be a single character in PHP 4. If a string is passed as the needle, then only the first character of that string will be used.</li></ul>

Of course, you have to use the strict equality operator <code>===</code> with those kind of functions, as you don't know if your results of 0 means false or a position of 0 with the weak typing of php without it.

Of course, there is a lot like.  PHP is incredibly pragmatic, and there is a ton of stuff in the standard library if you take the time to look.  The regex support is great.  Its zero deployment on mac or linux platforms - my macbook had apache and php all set and ready to go - just uncomment to lines in httpd.conf.  Php.net allows comments on its documentation, something that Sun should've done from the start to avoid the fragmentation you see amonst the different javadoc sitest that do this.

as an aside, I still haven't found a book that is the <a href="http://www.amazon.com/exec/obidos/redirect?tag=panasonicyout-20%26link_code=xm2%26camp=2025%26creative=165953%26path=http://www.amazon.com/gp/redirect.html%253fASIN=0201310058%2526tag=panasonicyout-20%2526lcode=xm2%2526cID=2025%2526ccmID=165953%2526location=/o/ASIN/0201310058%25253FSubscriptionId=0EMV44A9A5YT1RVDGZ82" title="View product details at Amazon">"Effective Java"</a> of the PHP world.  Please comment if you have suggestions.
