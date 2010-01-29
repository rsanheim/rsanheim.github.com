--- 
wordpress_id: 374
layout: post
title: Staging Environments in Rails
wordpress_url: http://robsanheim.com/2008/03/11/staging-environments-in-rails/
---
<p class="right img"><img id="alltheworldsastage..." src="http://farm1.static.flickr.com/57/165488318_e85a287039_m.jpg" alt="all the worlds a stage..." title="" /><br /> (<a style="font-size:75%" href="http://www.flickr.com/photos/wvs/165488318/" title="R. Fraser Elliott Hall on Flickr - Photo Sharing!">photo @ flickr</a>)</p>

<p>Most Rails apps that grow beyond the &#8220;toy&#8221; or &#8220;small&#8221; stage benefit greatly from the addition of a staging environment.  Staging is where you deploy to flush out integration issues, to demo new features to users and clients, and generally put the app through its paces in a &#8220;production-like&#8221; environment before doing a real production deployment.  It should match the production environment as closely as possible, though in practice things do diverge for certain cases and for most apps the cost of truly duplicating production hardware is prohibitive.</p>

<p>Rails lets you setup a staging environment easily.  Create a file in config/environments called &#8216;staging.rb&#8217;, and then start your server(s) with RAILS_ENV=staging, and you are all set.  Here&#8217;s quick steps to get up and running with a staging environment:</p>

<ol>
<li>copy config/environments/production.rb to staging.rb</li>
<li>add an entry to database.yml for staging</li>
<li><p>tweak your deployment to respect your new environment using <a href="http://weblog.jamisbuck.org/2007/7/23/capistrano-multistage">multistage</a> or something simple like this:<br />[ruby]
task :production do
  set :rails_env, "production"
  role :web, "prod.ip.here"
  # other roles...
end

task :staging do
  set :rails_env, "staging"
  role :web, "stage.ip.here"
  # other roles
end[/ruby]</p></li>
<li><p>setup and deploy staging: <pre>cap staging setup; cap staging deploy:cold; etc...</pre></p></li>
<li>tweak and iterate as you see fit</li>
</ol>

<p>You may ask at this point &#8220;why not just a copy of my production stack as staging?&#8221;  The fundamental reason is that <em>abstractions leak</em>.  Your staging environment is <em>similar</em> to production, but its not an exact copy.  Think about email notifications - do you really want exception notifications or activation messages to be send the same in staging as production?  Usually the answer is no - you want to be able to tell immediately if an error is from prod or staging, which could mean prepending [STG] in the subject and maybe changing the sender to be staging@domain.com.  For a lot of apps, you will have tasks that will perform differently between staging and production.  Some typical processes like this includes batch jobs, web service calls, and all sorts of notification jobs that would notify users or do a real external call, but in staging should just do a fake call and log the result.</p>

<p>To enable easier testing and cleaner code, a very simple wrapper class around RAILS_ENV is nice to have.  It also makes me happier to have less constants in my code, as I feel all caps detracts from the beauty of Ruby.  You can use <a href="http://blog.codahale.com/2006/04/09/rails-environments-a-plugin-for-well-rails/" title="Rails Environments: a plugin for, well, Rails | Archives | codablog | Coda Hale">Coda&#8217;s plugin</a> or write your own in probably 5 minutes.  Since you have a level of indirection around your environment checks, you can write specs like this:</p>

[ruby]it "should only log notifier emails in staging" do
  Rails.stubs(:staging).returns(true)
  AppNotifier.expects(:debug).returns(mock("logger", :debug =&gt; "some logger call"))
  AppNotifier.send_reports
end

it "should send emails in production" do
  Rails.stubs(:production).returns(true)
  AppMailer.expects(:deliver_reports)
  AppNotifier.send_reports
end
[/ruby]

<p>So don&#8217;t be afraid to create a separate staging environment and give it the respect it deserves when your deployment is complex enough to demand it.  It will make your life easier and your app easier to maintain and scale.</p>
