--- 
wordpress_id: 17
layout: post
title: Notes on synchronzied methods and code blocks
wordpress_url: https://www.robsanheim.com/?p=17
---
Just making some notes on the use of sychronized.  

[java]public void synchronized doStuff() {
// do stuff
}[/java]

..is equivalent to:

[java]public void doStuff{} {
  synchronized(this) {
  // do stuff
  }
}[/java]

The lock is on the object instance.  Any synchronized instance methods will be locked out while doStuff()  processes.  For static methods:

[java]public static void synchronized doStuff() {
// do stuff
}[/java]

is the same as:

[java]public static void doStuff() {
  synchronized(ThisClass.class) {
  // do stuff
  }
}[/java]

in that the lock is on the class object.  Further reading:
* <a href="https://mindprod.com/jgloss/synchronized.html">Synchronzied at mindprod</a>
* <a href="https://mindprod.com/jgloss/thread.html">Threads at mindprod</a>
* <a href="https://www.onjava.com/lpt/a/5245">Advanced Synchronization in Java</a>
* the excellent article <a href="https://www.cs.umd.edu/~pugh/java/memoryModel/DoubleCheckedLocking.html">Double Checked Locking is Broken</a>
