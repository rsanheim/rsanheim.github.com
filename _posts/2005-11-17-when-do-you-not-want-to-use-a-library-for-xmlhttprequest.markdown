--- 
wordpress_id: 116
layout: post
title: When do you NOT want to use a library for XmlHttpRequest?
wordpress_url: https://www.robsanheim.com/?p=116
---
Simple question - assuming we are talking about an app that is at least moderately sized (not a one-off or prototype), when would you <strong>not</strong> want to use a library or some sort of wrapper around the <a href="https://developer.apple.com/internet/webcontent/xmlhttpreq.html">XmlHttpRequest</a> object?  

I had some discussions at work recently about this, where I was pushing for <a href="https://www.getahead.ltd.uk/dwr/">DWR</a> and others were pushing for doing straight XHR to Struts actions keep it simpler with "one architecture" for less experienced developers.

What do you think?

<blockquote>(also: yet another way to do xhr, <a href="https://blog.fueledsoftware.com/2005/11/15/simple-ajax-code-kit-fixed/">via fueled software</a> (btw, why not use for...each?))[javascript]
this.createAJAX = function() {
    this.failed = true;
    try {
      this.xmlhttp = new XMLHttpRequest();
      this.failed = false;
    } catch (e) {
      var progIds = ['MSXML2.XMLHTTP', 'Microsoft.XMLHTTP', 'MSXML2.XMLHTTP.5.0', 'MSXML2.XMLHTTP.4.0', 'MSXML2.XMLHTTP.3.0'];

      for (var iterator = 0; (iterator < progIds.length) && ( ! this.success); iterator ++) {
        try {
          this.xmlhttp = new ActiveXObject(progIds[iterator]);
          this.failed = false;
        } catch (e) {}
      }
    }
  };
[/javascript]</blockquote>

</blockquote>
