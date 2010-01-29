--- 
wordpress_id: 253
layout: post
title: Hacking green bar color output into Autotest
wordpress_url: http://www.robsanheim.com/?p=253
---
<strong>update:</strong> You don't need to do this hack anymore - the RedGreen plugin is builtin into autotest with the latest versions.

A much welcome <a href="http://blog.zenspider.com/archives/2006/07/autotest_no_lon.html">upgrade</a> of the indispensable <a href="http://www.zenspider.com/ZSS/Products/ZenTest/">autotest</a> recently came out which speeds things up greatly, but the output was still plain test_unit output.  There are now hooks to add plugins to add widgets or whatever crazy output you want, but all I wanted was a green or red bar in the console.  Taking some help from <a href="http://on-ruby.blogspot.com/2006/05/red-and-green-for-ruby.html">RedGreen</a> by Pat Eyler for the escape chars, here's out make your autotest output a bit more feedbackie:

add this to the utility section of autotest.rb (yes, just hack the gem - its a minor change and the codebase is simple enough):

[ruby]
 BAR = "=" * 80

  # filter output for colorized green/red bar
  def filter_output(results)
    filtered = ""
    results.each do |line|

      if line =~ /\d+ tests, \d+ assertions, 0 failures, 0 errors/
        line = "\e[32m#{BAR}\n#{$&}\e[0m\n\n"
      elsif line =~ /\d+ tests, \d+ assertions, (\d+) failures, (\d+) errors/
        if $1 != 0 || $2 != 0
          line =  "\e[31m#{BAR}\n#{$&}\e[0m\n\n"
        end
      end
      filtered < < line
    end
    filtered
  end
[/ruby]

Then change the method "run_tests" to call filter output:

[ruby]
def run_tests
....
    @results = `#{cmd}`
    hook :ran_command
    puts filter_output(@results)
....
[/ruby]

And you'll have output like this:

<img src='/wp-content/autotest_red_green.jpg' alt='autotest red green outpout' />
