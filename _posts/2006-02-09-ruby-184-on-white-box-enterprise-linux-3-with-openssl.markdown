--- 
wordpress_id: 191
layout: post
title: Ruby 1.8.4 on White Box Enterprise Linux 3 (with OpenSSL)
wordpress_url: https://www.robsanheim.com/?p=191
---
Finally figured out why ruby wasn't picking up openssl when I was installing it from the tarball.  This was resulting in <a href="manuals.rubyonrails.com/read/book/17">switchtower</a> not working, which was really driving me crazy as I'm trying to get this box ready for deployments.  Well, I guess I'm not sure exactly what is going on, but <a href="https://blade.nagaokaut.ac.jp/cgi-bin/scat.rb/ruby/ruby-talk/118223">this thread</a> on ruby-talk pointed me to what I had to do before make:

<code>export CPPFLAGS="-I/usr/kerberos/include"
export LDFLAGS="-L/usr/kerberos/lib"
./configure
</code>

Once I did that, this finally worked:
<code>irb(main):001:0> require 'openssl'
=> true</code>

Which was really what this was all about.  Now I'm just hoping this doesn't upset some other dependency down the road...


