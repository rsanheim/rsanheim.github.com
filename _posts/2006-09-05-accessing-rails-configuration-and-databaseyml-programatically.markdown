--- 
wordpress_id: 263
layout: post
title: Accessing Rails Configuration and database.yml Programatically
wordpress_url: https://www.robsanheim.com/?p=263
---
I changed our database.yml to use <a href="https://redhanded.hobix.com/bits/yamlSMergeKey.html">merge keys</a>, but we have a case where the host is different for production from all the other environments.  I wanted to test and ensure the prod db host remained correct with the yaml merge - the docs say it works like hash#merge, but you don't wanna mess around with your production environment. 

So here's how to access your configuration programmatically, so you can test it - note that "database_configuration" is a hash with the values from database.yml.

[ruby]def test_db_host_configuration
  config = Rails::Configuration.new
  assert_equal "prod_host", config.database_configuration["production"]["host"]
  assert_equal "prod_host", config.database_configuration["other_production"]["host"]
  assert_equal "localhost", config.database_configuration["development"]["host"]
  ... # etc
end[/ruby]

Take at a look at initalizer.rb in the rails source to see what is all on the configuration object, you can lots of useful stuff there.  Note that this is creating a new config object, not reading the in-memory one, so I suppose if you do crazy stuff like modify config values on the fly this wouldn't be reliable.  
