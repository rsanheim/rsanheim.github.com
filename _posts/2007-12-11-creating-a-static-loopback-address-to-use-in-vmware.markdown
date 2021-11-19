--- 
wordpress_id: 353
layout: post
title: Creating a Static Loopback Address to use in VMWare
wordpress_url: https://robsanheim.com/2007/12/11/creating-a-static-loopback-address-to-use-in-vmware/
---
The problem: you want to be able to always use the same address in VMWare Fusion for your local Mac web server(s), to test IE6 and IE7 with apps as you dev locally.  You normally connect via DHCP, so you can't depend on your IP address being constant.  You can't use localhost or 127.0.0.1 within VMWare, because that just points back to the Windows box.  

Annoying manual solution: Everytime you fire up VMWare to work in IE you need to copy your ip from the Mac side and paste it into IE, adding https:// to the front and the port on the back.  This an annoying manual process that doesn't seem like it should be necessary.  Searching vmware's site and forums doesn't turn up much, and using the local hostname is unreliable.  

<strong>The awesome solution:</strong> Setup an an additional IP pointing at the loopback interface, which will allow always connecting to your Mac from within VMWare, regardless of your internet connectivity.  Run the following line from terminal to do this:

<code>sudo ifconfig lo0 inet 10.0.0.100 netmask 255.255.255.0 alias</code>

Start up some server locally, and hit https://10.0.0.100 - it should work both from your Mac and within VMWare fusion.  (You can substitute any <a href="https://en.wikipedia.org/wiki/Private_network">private IP</a> for the 10.0.0.100 address)

To make this change persistent, add the line above, without the sudo in front, to your <strong>/etc/rc.local</strong> file.  

update: Wade <a href="https://www.lunenburg.org/wade/articles/2007/12/11/theres-no-place-like-lo0">blogged his experience</a> on figuring this out from the sysadmin side.  Thanks Wade!
