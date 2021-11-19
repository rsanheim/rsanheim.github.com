--- 
wordpress_id: 27
layout: post
title: You know your cache is slowing development when...
wordpress_url: https://www.robsanheim.com/?p=27
---
You see this in your logs:

<code>[7/22/05 15:30:27:272 CDT] 10431043 ThreadMonitor W WSVR0605W: Thread "Servlet.Engine.Transports : 0" (35b135b1) has been active for 767,637 milliseconds and may be hung.  There are 1 threads in total in the server that may be hung.
[7/22/05 15:33:34:094 CDT] 35b135b1 ThreadMonitor W WSVR0606W: Thread "Servlet.Engine.Transports : 0" (35b135b1) was previously reported to be hung but has completed.  It was active for approximately 954,459 milliseconds.  There are 0 threads in total in the server that still may be hung.</code>

<em>(sigh)</em>
