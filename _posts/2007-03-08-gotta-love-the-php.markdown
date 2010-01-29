--- 
wordpress_id: 304
layout: post
title: Gotta love the PHP
wordpress_url: http://www.robsanheim.com/?p=304
---
Quick - what does this line of PHP do:

[php]@ $value = unserialize($option->option_value);[/php]

Look, its an 'at sign'.  Hmm...that must be something special.  I bet its some really advanced crazy PHP feat...oh <strong>of course</strong> - its PHP's <a href="http://www.php.net/manual/en/language.operators.errorcontrol.php">error control</a>!  it tells the intrepeter to ignore any and all errors in that line of code!  This warning from the docs is cool:

<blockquote>Currently the "@" error-control operator prefix will even disable error reporting for critical errors that will terminate script execution. Among other things, this means that if you use "@" to suppress errors from a certain function and either it isn't available or has been mistyped, the script will die right there with no indication as to why. </blockquote>

Thank you PHP language designers, for creating such readable, obvious code.  Between the @ operator and the awesome function names, I don't know what I love more about php.
