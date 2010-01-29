--- 
wordpress_id: 96
layout: post
title: moo.fx - lightweight javascript effects built on Prototype
excerpt: ultratiny alternative to scriptaculous
wordpress_url: http://www.robsanheim.com/?p=96
---
Is  <a href="http://script.aculo.us/">scriptaculous</a> overkill for the quick web app you are writing?  Then check out <a href="http://moofx.mad4milk.net/">moo.fx</a>, a 3kb (!) file that extends <a href="http://www.robsanheim.com/2005/08/23/prototype-javascript-library-documentation/">Prototype</a> to do some very smooth, effective transitions.  Moo.fx handles height, width, and opacity, and does it with some very simple code: 
[javascript]
 window.onload = function(){
 var effect = new fx.Height('myelement',{duration:400,
  onComplete: function(){
   alert('the effect is finished');
  }
 });
}[/javascript]
The above snippet registers the height effect on 'myelement' onload - then you're free to call the toggle method or a custom method on whatever events you want.  Take a look at the <a href="http://moofx.mad4milk.net/tests.html">demo page</a> to see this stuff in action.

(Via <a href="http://redhanded.hobix.com/inspect/fadingRollupsIn3k.html">why the luck the stiff</a>)
