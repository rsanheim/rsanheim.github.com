--- 
wordpress_id: 69
layout: post
title: "IDE code smell:  generated comment templates in repository"
wordpress_url: https://www.robsanheim.com/?p=69
---
Many of the modern automated IDEs insert boilerplate comments into your code as your create new classes, methods, code blocks, etc.  They contain something like the following: 

<code>/*
 * Created on Aug 15, 2005
 *
 * @author Insert Name Here
 * Insert type description here
 *
 * To change the template for this generated file go to
 * Window&gt;Preferences&gt;Java&gt;Code Generation&gt;Code and Comments
 */</code>

These comments are meant to be a edited by the developer before being used.  The problem arises when code containing these templates is checked into the repository.  Seeing these templates indicates that the code wasn't reviewed before check in, and could also be a sign of a straight "copy-paste-checkin".  It could also be a sign of a junior developer whose code is not being reviewed when it should be.  If you have enough of these left in the repository, you will soon have a lot of <a href="https://c2.com/cgi/wiki?FixBrokenWindows">broken windows</a> around and no one will care enough to keep their comments updated or correct.

Therefore, make sure all developers on a team are trained to update the generated comments to match the team standard.  Ensure that only the required comment headers will be inserted, and that all developers know to update the comments before check in.  Make sure to keep the comments as short and simple as possible - if there is a 15 line prolog for every class, entropy will win easily.  Seeing one or two generated comments is an understandable mistake, while a repeated pattern is a smell to be corrected.

<h3>Applicable Positive Patterns:</h3>
<ul>
<li><a href="https://www.stickyminds.com/s.asp?F=S9041_ART_3">Write Sweet Smelling Comments</a></li>
<li><a href="https://c2.com/cgi/wiki?PairProgramming">Pair Programming</a></li>
<li><a href="https://c2.com/cgi/wiki?PeerReview">Peer Review</a></li>
<li><a href="https://c2.com/cgi/wiki?CodeReviewDay">Code Review Day</a></li>
</ul>
