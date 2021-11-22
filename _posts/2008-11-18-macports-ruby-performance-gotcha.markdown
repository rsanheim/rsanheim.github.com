--- 
wordpress_id: 402
layout: post
title: MacPorts Ruby performance gotcha
wordpress_url: https://robsanheim.com/?p=402
---
<p>If you install Ruby from MacPorts (all the cool kids do), be aware that the first 1.8.7 port had some issues that basically broke performance, making it run three times slower than normal.  Verify that you have the <code>1.8.7-p72_2</code> version active, and not <code>1.8.7-p72_1</code>:</p>

  ```
> sudo port installed |grep ruby
ruby @1.8.7-p72_1+thread_hooks
ruby @1.8.7-p72_2+thread_hooks (active)
```

<p>The <a href="https://trac.macports.org/ticket/17092" title="#17092 (Ruby 1.8.7 is 3x slower than its predecessor) – MacPorts – Trac">defect on MacPorts Trac</a> has more details, along with links to a relevant <a href="https://groups.google.com/group/ruby-talk-google/browse_thread/thread/2b326089f18f2b29/49b69aca0f5112e8?lnk=gst&amp;q=macports#49b69aca0f5112e8">ruby-talk thread</a>.  </p>

<p>Its worth pointing out that this issue went from discovery to being fixed and released into the port stream in about a days time.  MacPorts has really come a long way from just a year or two ago.  Fairly major packages used to lag behind the latest stable releases by multiple versions, but now I find everything I care about stays up to date with ease from MacPorts.  They are even able to keep up with <a href="https://www.macports.org/ports.php?by=name&amp;substr=git-core" title="The MacPorts Project -- Available Ports">git releases</a>, an impressive task considering how fast and furious releases git releases come.  </p>

<p>Kudos to the <a href="https://www.macports.org/ports.php?by=name&amp;substr=git-core" title="The MacPorts Project -- Available Ports">MacPorts team</a> for doing a fine job and making developers' lives easier.</p>
