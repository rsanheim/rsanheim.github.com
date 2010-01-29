--- 
wordpress_id: 133
layout: post
title: DHH on Rails and Django
wordpress_url: http://www.robsanheim.com/?p=133
---
The creator of Rails <a href="http://www.loudthinking.com/arc/000545.html">talks about</a> the recent <a href="http://snakesandrubies.com/event/">Snakes and Rubies</a> event in Chicago this last Saturday.  The thing that really strikes me (besides the <a href="http://media.rubyonrails.org/presentations/pursuitofbeauty.pdf"> very cool presentation [PDF] </a> David gave) is the Django vs Rails code:

<pre><code>
class Project(meta.Model):
  project_manager = meta.ForeignKey(ProjectManager)
  milestones = meta.OneToOneField(Milestone)
  categories = meta.ManyToManyField(Category)
 
p  = projects.get_object(id__exact=1)
pp = projects.get_list
</code></pre>

The Python code looks <strong>a lot</strong> like Java code to me.

<pre><code>
class Person < ActiveRecord::Base
  belongs_to :project_manager
  has_many   :milestones
  has_and_belongs_to_many :categories
end
 
p  = Project.find(1)
pp = Project.find(:all)
</code></code></pre>

And of course the Ruby code is much prettier to me, and I would much rather work with it on a day to day basis.  Such is the beauty of <a href="http://galbraiths.org/blog/?p=19">DSL's</a> I suppose.
