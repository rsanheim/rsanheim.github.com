--- 
wordpress_id: 35
layout: post
title: Fowler on collections and closures
wordpress_url: https://www.robsanheim.com/?p=35
---
<a href="https://martinfowler.com/bliki/CollectionClosureMethod.html">Martin Fowler blogged</a> on how Ruby deals with collections using blocks (or closures).  Its a nice example of some of the power you really miss having in the Java/C# family of languages.  

Wouldn't it be nice if instead of this:
[java]
List managers = new ArrayList();
for(Iterator iter = employee.iterator(); iter.hasNext();) {
   Employee emp = (Employee) iter.next();
   if(emp.isManager()) 
       managers.add(emp);
}
[/java]

You could just do this:
[java]
List managers = new ArrayList();
managers.addAll( employee.find{ |e| e.isManager() });
[/java]

On a related note, is there any difference between a "closure" and a "block" in Ruby?
