--- 
wordpress_id: 216
layout: post
title: IDEA vs Textmate, and Rails 1.1 web services
wordpress_url: https://www.robsanheim.com/?p=216
---
Patrick has a <a href="https://blogs.opensymphony.com/plightbo/2006/03/teaching_mr_rails_a_lesson_on.html">well-reasoned comparison</a> of IntelliJ IDEA and Textmate and how well this work with HTML/CSS.  IDEA wins out for code completion and error highlighting, but Textmate wins for its light footprint and speed.  Its good to see a balanced comparison of tools from someone who works with both.

Jamis <a href="https://jamis.jamisbuck.org/articles/2006/03/27/web-services-rails-style">highlights</a> how easy it is to add web-services to your models in Rails 1.1, allowing you to do a simple xml web service with just this:
[ruby]def list
    @people = Person.find(:all)

    respond_to do |wants|
      wants.html
      wants.xml { render :xml => @people.to_xml }
    end
  end[/ruby]

Very nice.
