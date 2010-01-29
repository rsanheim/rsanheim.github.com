--- 
wordpress_id: 57
layout: post
title: preferred Iterator usage - use "for", not "while"
excerpt: using "while" with Iterators is naughty
wordpress_url: http://www.robsanheim.com/?p=57
---
<strong>Note:</strong> this tip not quite as applicable with Java 5.

One of my pet peeves is coming up this loop construct for iteration - don't use this:

[java]
Iterator iter = widgets.iterator();
while(iter.hasNext()) {
    foo(widgets.next());
}[/java]

Instead, use the "for loop idiom".  It minimizes the scope of the iterator and is a safer, shorter, and is clearer:

[java]for(Iterator iter = widgets.iterator(); iter.hasNext();) {
    foo(widgets.next());
}[/java]


Good ole' <a href="http://www.amazon.com/exec/obidos/redirect?tag=manalangcom-20%26link_code=xm2%26camp=2025%26creative=165953%26path=http://www.amazon.com/gp/redirect.html%253fASIN=0201310058%2526tag=manalangcom-20%2526lcode=xm2%2526cID=2025%2526ccmID=165953%2526location=/o/ASIN/0201310058%25253FSubscriptionId=0EMV44A9A5YT1RVDGZ82" title="View product details at Amazon">Effective Java</a> has a nice example of the kind of copy-and-paste bugs that can happen with the first idiom:

[java]Iterator i = c.iterator();
while(i.hasNext()) {
    foo(i.next());
}
// other code
Iterator i2 = c2.iterator();
while(i.hasNext()) {
    foo(i2.hasNext());
}[/java]

Do you see the bug?  Its easy to see here, of course, but could be tough to find in practice as it runs fine but just functions incorrectly.  It would be a compile time error if you went with the for construct.  Its always best to keep your variable scope as small as possible, and the for loop also makes refactoring cleaner if you want to extract the loop block out.
