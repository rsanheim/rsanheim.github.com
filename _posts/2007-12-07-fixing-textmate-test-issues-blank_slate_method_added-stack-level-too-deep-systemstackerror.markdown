--- 
wordpress_id: 352
layout: post
title: "Fixing Textmate Test Issues - `blank_slate_method_added': stack level too deep (SystemStackError)"
wordpress_url: https://robsanheim.com/2007/12/07/fixing-textmate-test-issues-blank_slate_method_added-stack-level-too-deep-systemstackerror/
---
If you are getting long, recursive stack traces like the following when trying to run a test/spec from within Textmate:

[ruby]/opt/local/lib/ruby/gems/1.8/gems/builder-2.1.2/lib/blankslate.rb:84:in `blank_slate_method_added': stack level too deep (SystemStackError)
from /opt/local/lib/ruby/gems/1.8/gems/builder-2.1.2/lib/blankslate.rb:84:in `blank_slate_method_added'
from /Applications/TextMate.app/Contents/SharedSupport/Support/lib/builder.rb:86:in `method_added'
from /Applications/TextMate.app/Contents/SharedSupport/Support/lib/builder.rb:111
from /opt/local/lib/ruby/vendor_ruby/1.8/rubygems/custom_require.rb:27:in `gem_original_require'...[/ruby]

The stack goes on for many more lines, and your tests always work normally outside of textmate.  The issue is that textmate includes its own version of builder, which is conflicting with Rails' version of builder.  

<strong>The solution is simple:</strong> rename Textmate's builder.rb to builder.rb.off, so it doesn't get loaded anymore.  You can find Textmate's builder at "/Applications/TextMate.app/Contents/SharedSupport/Support/lib/Builder.rb". Problem solved.  See also this <a href="https://macromates.com/ticket/show?ticket_id=F4DA8B03">support thread</a> with some more detail.
