--- 
wordpress_id: 259
layout: post
title: Rails Schema Dumper + Mysql ENUM's = Bad For Business
wordpress_url: http://www.robsanheim.com/?p=259
---
Yesterday was burned on trying to get our legacy database working again with Rails.  I say "again" as we already had things working with a dual db setup - where the legacy stuff was just always there and never needed to be re-created via schema dump and "rake clone_db_structure".  The plan was to throw all the tables together into the legacy database, remove the AlternateDatabase hacks, tweak the db to remove enum's we were indexing on, merge/create all that into one database, and flip the switch to be on one database.  Of course, things never go that smoothly...in the process I learned more about what actually happens you type "rake", why enums are bad, and the importance of checking the obvious.

My problems started with test failures that <a href="http://jameshalberg.wordpress.com/">Jim</a> wasn't getting - which initially made me think I had made an error in the process of copying and munging local databases.  After some retries, ensuring I was fully up to date, and some help from Jim in making sure I had the process right, I still had errors and yet Jim's machine passed all tests just fine.  Looking through the logs revealed different mysql errors, but I was confused as to why I would be the only one to get them.  Thats the worst kind of failure.

Finally, I got smart and asked for Jim's mysql version.  His was 4.0.something, mine was 5.0.16.    A hah - a prime suspect.  I knew from experience that mysql's engine tends to be very lax with constraints and keys, particularily with earlier versions when it was less enterprisey.  So now I realized it was probably something that Rails' schema dumper created in schema.rb that Mysql 5 hated but Mysql 4 was okay with.  And it was - in schema.rb I saw multiple fields like this:

[ruby]t.column "some_status", :string, :limit => 0, :null => false, :default => 'Y'[/ruby]

So we had a string column with a zero length (or limit) but a default value - obviously these constraints don't make sense, and Mysql errors out on it.  Mysql 4 just went on cruising with it for Jim, probably ignoring the default silently.  Eventually, we changed every single Enum column in the legacy dev database to an equivalent varchar column.  This allowed the schema dumper to create a valid schema.rb, which would then be used by rake for creating the test database and running everything.  Green bar, finally.

Lessons Learned:
<ul><li><a href="http://wiki.rubyonrails.com/rails/pages/HowtoUseSetAndEnumColumns">ActiveRecord doesn't like Enums</a> - we initially thought we would be okay by just changing the enums that were part of indexes.  We were wrong.  Don't use enums and watch out for legacy tables with them.</li>
<li>Schema dumper silently converts enums into string fields with a length of zero, so be careful as your DB could very well error out on it.  Someone should <a href="http://dev.rubyonrails.org/ticket/2379">update and apply this patch</a> so there is more warning!</li>
<li>Don't just rely on autotest for the health of your code - run the full rake too, as there are slight differences that can result in failures in one and not the other.</li>
<li>Make sure everyone is on the same version of everything for their dev environment.  This should be an obvious first step, but I overlooked it.</li>
</ul>
