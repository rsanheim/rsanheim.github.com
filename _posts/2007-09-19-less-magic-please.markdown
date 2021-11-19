--- 
wordpress_id: 339
layout: post
title: Less Magic, Please
wordpress_url: https://robsanheim.com/2007/09/19/less-magic-please/
---
My development style tends towards less and less metaprogramming and magic these days.  Its not for lack of ability or lack of capable coworkers.  I work with some <a href="https://relevancellc.com/">pretty sharp</a> people, and I know they can grok whatever sort of voodoo method_missing module_eval mysticism I can throw at them.  But lately I feel that the value of explicit, clean, simple, well factored code outweighs the benefits of of a clever API or a terse one liner that comes from the metaprogramming typically found in Ruby and Rails these days.  

I'm sure some of this comes from growing weary of reading plugins or open source code that just takes longer to understand than it really should.  Maybe the magic made sense for the first iteration to save some time, and sometimes its just being clever for clever's sake.  Regardless, the code you write is not your own.  It has to be read and understand and changed by future developers, people who may be coming to the program with much less knowledge of the domain AND the language.  It has to be explained to coworkers when code reviews or pairing comes up, and possibly documented and written about for the open source community.  Think about them and take the extra 10 minutes to refactor to something that you could easily explain or write about in a sentence or two to an average developer.  

With specs or test cases, being clear and explicit is even more critical.  I remember in my Java days I used to follow the philosophy that all code, even tests, should follow the same quality standards.  So I tried to keep my tests just as DRY as my production code.  Now my thinking is similar to what Jay Fields talks about with <a href="https://blog.jayfields.com/2007/06/testing-inline-setup.html">inline setup</a> - keep as much as setup right in the test as possible.  If there is too much setup to do so, its a smell that you are testing too much or your unit under test is not well factored.  

The Ruby community takes much pride in the dynamism and power of the language, and how easily you can modify things at runtime or alias and hack in your versions of methods.  Anyone who has read the call chain of much of Rails' internals that uses alias_method_chain knows what happens when this power goes unchecked.  You get layers upon layers of x_without_foo, x_with_foo, before_x_with_foo, into a never ending rabbit hole which makes any sort of extension or plugins horrible.  When you have over two aliased versions of the same method, thats probably a good sign that its time to refactor to a full blown decorator and make the extension point first class.

How to actually put this into practice?  I know as well as anyone the temptation of clever code, of playing with method_missing or meta_eval when you are heads down in a tricky problem.  

<ul>
<li>Pair program - ask your pair if your code is clear enough.  If your pair has been on the same code base as you for a long time, ask someone else who would have a fresher look.  Rotating pairs is probably the best way to fight too-clever code.</li>
<li>Code reviews - ie "pair program lite."</li>
<li>Explain your code to the nearby stuffed animal, or rubber ducky, or whatever.  If you can't find the words for it easily, take a second look.</li>
<li>Look for code smells - lots of comments, difficulty with testing, premature generalization, excessive use of any of the evals, or high <a href="https://ruby.sadi.st/Flog.html">flog</a> scores.</li>
<li>Walk away, go outside, take at least a fifteen minute break from the code.  Sometimes it just takes some distance and perspective to realize where a more direct, plain approach is best.</li></ul>
