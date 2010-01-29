--- 
wordpress_id: 234
layout: post
title: Browser bugs - onblur and onfocus with IFrames
excerpt: Getting onblur and onfocus to attach to Iframes in IE and Firefox/Mozilla/Gecko...
wordpress_url: http://www.robsanheim.com/?p=234
---
This is one of those cross browser issues that you think you should be able to find via Google within five minutes, but ends up taking much longer.  Maybe I was using poor search queries, or maybe I'm just having an off day.  Anyways, maybe this will helpful for someone in the future...

I'm using a rich editor widget, <a href="http://tinymce.moxiecode.com/">TinyMCE</a>, and have been trying to attach validation to the editor onblur.  The documentation at MCE's website was spotty at best, with most suggestions saying "write a plugin" for something that should not be that complicated.  So I decided to try and attach the handler directly to the iframe that tinymce is using under the covers for its magic.  So here is the first, simple attempt:

[javascript]var theFrame = $('mce_editor_0');
Event.observe(theFrame.contentDocument, 'blur', testIt);[/javascript]

...Which only worked in IE6, not in FF (mac or win).  This is the point where I should have stopped and just gone to the <a href="http://www.mozilla.org/docs/dom/domref/dom_frame_ref13.html#998139">IFrame part</a> at the Gecko Dom page, as the lack of any events on the element would've tipped me off.  But I didn't.  I went to google and tried a bunch of queries: "iframe onblur", "iframe onblur event", "attach events iframe", etc.  This got me a lot of stuff about different ways to access iframes to make old browsers happy, and a bunch of stuff about design mode and rich text editing, but nothing about where the heck to attack handlers for onblur or onfocus (or anything else) in Gecko vs IE.

Then I just went to <a href="http://www.joehewitt.com/software/firebug/">Firebug</a> and did some inspecting on the actual iframe, and through trial and error found the ridiculously simple solution - attach events to contentdocument.  In code: 

[javascript]
var theFrame = $('mce_editor_0');
if(theFrame.contentDocument) {
	Event.observe(theFrame.contentDocument, 'blur', testIt);
} else {
	Event.observe(theFrame, 'blur', testIt);
}[/javascript]

Totally simple, and if you have hit this snag its probably second nature.  The first time, though, its pretty painful.  And of course, this still <a href="http://ajaxian.com/archives/give-safari-some-love>doesn't work in Safari.</a>
