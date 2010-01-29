--- 
wordpress_id: 254
layout: post
title: Using Autotest with Integration Tests
wordpress_url: http://www.robsanheim.com/?p=254
---
Autotest by default doesn't try to do anything with integration tests...since they can test so many files, its impossible to map x controller and z model to a integration test.  However, that shouldn't prevent it from at least rerunning an integration test when there are changes to the integration test itself, and also running the integration test when it does the whole suite run.  So in rails_autotest.rb you can add another case to the tests_for_file method:

[ruby]
    when %r%^test/integration/.*\.rb$% then
      [filename]
[/ruby]

Which just means "include integration tests in the suite, and rerun the integration test when it changes."
