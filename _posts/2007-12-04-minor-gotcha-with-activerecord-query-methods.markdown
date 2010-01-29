--- 
wordpress_id: 350
layout: post
title: Minor Gotcha with ActiveRecord query methods
wordpress_url: http://robsanheim.com/2007/12/04/minor-gotcha-with-activerecord-query-methods/
---
Stumbled upon a gotcha with the ActiveRecord query methods you get for free, along side the normal attribute accessor methods.  Its a "gotcha" in that I "gotcha" read the docs and Rails source a bit more in depth before making assumptions about how Rails works, but I'd rather pretend the <a href="http://www.koziarski.net/archives/2007/12/1/they">fault is with Rails</a> for my self esteem.

So you get the accessors and a query method (ie question method) for all attributes in a model.  The query method seems to just return true or false based on if the field is populated or not:

[ruby]
>> u = User.new
>> u.email?
=> false
>> u.email = "your@mom.com"
=> "your@mom.com"
>> u.email?
=> true
>> u.email = "anything"
=> "anything"
>> u.email?
=> true
[/ruby]

At least thats what I assumed a long time ago, without looking into things enough.  Recently, I had a model that was supposed only to validate the email field if it was populated.  I'm not using edge for this project, so I couldn't use <a href="http://dev.rubyonrails.org/ticket/7383">allow_blank</a> -- so I had something like this:

[ruby]
# in da model
  validates_format_of     :reminder_email,
                          :with => /.+@.+\..+/,
                          :if => lambda {reminder_email?} 
# in da spec
  User.new(:email => "f").should.not.validate # wtf, why doesn't this fail?  
[/ruby]

When it comes to things done with metaprogramming in ActiveRecord, I tend to go straight to the source instead of trying to research in the docs.  Sure enough, the code was pretty straight forward - AR is giving me a query method assuming a string represents some sort of boolean field...its not testing existance at all!

[ruby]
# define_question_method gets called for each non primary key attribute, 
# which eventually creates the query method like so:
      def query_attribute(attr_name)
        attribute = @attributes[attr_name]
        if attribute.kind_of?(Fixnum) && attribute == 0
          false
        elsif attribute.kind_of?(String) && attribute == "0"
          false
        elsif attribute.kind_of?(String) && attribute.empty?
          false
        elsif attribute.nil?
          false
        elsif attribute == false
          false
        elsif attribute == "f"
          false
        elsif attribute == "false"
          false
        else
          true
        end
      end
[/ruby]

So if your field is a string and a value like "f", "false", or "0", the query method will return false.  Hence my validation was never getting triggered for my spec, as the bad email I supplied was "f".  

The fix is simple - just test that the attribute was not blank for the validation if block:
[ruby]:if => lambda {!reminder_email.blank?} [/ruby]

The takeaway for me on this is a common one - when something is wrong, question your assumptions first, then question them again.  Also, keep the Rails source close at hand.  The docs have been improving, but they still fall down in some areas.  A cursory glance over <a href="http://api.rubyonrails.com/classes/ActiveRecord/Base.html">ActiveRecord::Base docs</a> showed nothing for these generated query methods. 
