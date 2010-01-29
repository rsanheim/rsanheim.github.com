--- 
wordpress_id: 355
layout: post
title: Handling asset caching nicely in Rails 2.0
wordpress_url: http://robsanheim.com/2007/12/13/handling-asset-caching-nicely-in-rails-20/
---
<strong>update:</strong> fix some incorrect paths that did not have the public in front.  (thanks Jon)

From your rails root:

<code>mkdir public/javascripts/cache
mkdir public/stylesheets/cache
svn add public/javascripts/cache/
svn add public/stylesheets/cache/
svn propset svn:ignore '*' public/javascripts/cache/
svn propset svn:ignore '*' public/stylesheets/cache/
svn ci -m "add cache directories for combined assets, but ignore their contents"</code>

Then wherever you are doing the js and css includes:

<code>< %= stylesheet_link_tag "application_v2", "foo_styles", :cache => "cache/styles" %>
< %= javascript_include_tag "prototype", "application", "foo", "bar", :cache => "cache/defaults" %></code>

Why do this?

<ul>
<li>it lets you flip perform_caching on locally without cluttering up your svn status with files you don't want to add (and you want to test asset caching locally cross-browser)</li>
<li>it lets you clear out the cached files with one command locally or on the server, instead of hunting and pecking for the cached files</li>
<li>it allows you to get really fancy, and push the cache folders into a shared directory so that they don't get blown away on each deploy -- obviously this would only make sense when your js/css has stabilized</li>
</ul>
