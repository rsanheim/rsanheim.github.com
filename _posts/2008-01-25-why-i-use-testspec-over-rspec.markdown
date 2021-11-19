--- 
wordpress_id: 362
layout: post
title: Why I use test/spec over rspec
wordpress_url: https://robsanheim.com/2008/01/25/why-i-use-testspec-over-rspec/
---
<blockquote><strong>...the worst thing that can happen to a code base is size.</strong> -- <a href="https://steve-yegge.blogspot.com/2007/12/codes-worst-enemy.html">Steve Yegge</a></blockquote>

<table>
  <tr>
    <td><strong>Project</strong></td>   <td><strong>LOC</strong></td>
</tr>
<tr>
    <td><a href="https://rspec.info/">RSpec</a></td>     <td>15581</td>
</tr>
<tr>
    <td><a href="https://chneukirchen.org/repos/testspec/README">test/spec</a></td> <td>1512</td>
</tr>
<tr>
    <td><a href="https://www.ruby-forum.com/topic/137928">bacon</a></td>     <td>477</td>
</tr>
</table>

<br />

<span style="font-size:x-small">(Lines of code counted with <a href="https://www.dwheeler.com/sloccount/">sloccount</a>, adding up only results from the lib and test (or spec) directories for each of the latest gems.)</span>
