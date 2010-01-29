--- 
wordpress_id: 359
layout: post
title: Rails observers make rake db:migrate crash from version 0
wordpress_url: http://robsanheim.com/2008/01/08/rails-observers-make-rake-dbmigrate-crash-from-version-0/
---
Rails observers are typically defined like this in environment.rb:

[ruby]
Rails::Initializer.run do |config|
  config.action_controller.session_store = :active_record_store
  config.active_record.observers = :user_observer
end
[/ruby]

I recently hit an issue where a fresh db:migrate of an app with a standard observer blew out every time.  After some digging into the trace, I saw it was due to rake loading environment.rb, which fires up the observer, which then loads the observed model -- which of course does not exist yet since the database is at version 0.  I'm guessing you won't always see this error, as the DB call is triggered by certain validations -- if your model is relatively free of validations I imagine you may be fine.

Some googling led me to <a href="http://www.jamesrobey.com/making-rake-tasks-ignore-rails-observers/">James Robey's proposed fix</a>, which as the downfall of disabling the observer for any call to rake.  This little hack should be a bit better, in that it will only disable the observer for rake db:migrate calls:

[ruby]
# observers break a migrate from VERSION 0 - disable them for rake db:migrate
unless ( File.basename($0) == "rake" && ARGV.include?("db:migrate") )  
  config.active_record.observers = :user_observer
end
[/ruby]

Go forth, and migrate from version 0 with impunity.
