--- 
wordpress_id: 248
layout: post
title: Testing named routes or url_for in functional test
wordpress_url: http://www.robsanheim.com/?p=248
---
If you've ever tried using <a href="http://wiki.rubyonrails.org/rails/pages/NamedRoutes">named routes</a> or url_for in functional tests, you might have seen an error like this:

<code style="font-size: 10px;">  1) Error:
test_article_override_to_meta(ArticleControllerTest):
NoMethodError: You have a nil object when you didn't expect it!
The error occured while evaluating nil.rewrite
    /usr/local/lib/ruby/gems/1.8/gems/actionpack-1.12.1/lib/action_controller/base.rb:461:in `url_for'
    generated/routing/named_routes/article.rb:2:in `article_url'
    /usr/local/lib/ruby/gems/1.8/gems/actionpack-1.12.1/lib/action_controller/test_process.rb:431:in `method_missing'
    test/functional/article_controller_test.rb:32:in `test_article_override_to_meta'</code>

What is happenening here is that ActionController uses the current request as its context for creating new urls, so for instance if you do <code>url_for :action => "create"</code> it will use the current controller from the current request.  So, if you write a functional test that tries kick things off with url_for (or a named route, which really just calls url_for under the covers) it fails as there is no current url.

Tracing into ActionController, @url gets created by a private method which is in the whole request cycle - so mocking it out probably isn't worth the trouble.

The solution is simple - call a simple, easy url (preferably without side effects - like index) before you use the named route or url_for.  For example:

[ruby]
def test_article_url
    get :index
    url = article_url :controller => "article", :id => 1234
    assert_equal "http://host/article/1234", url
end
[/ruby]

If you wanted to keep this drier you could move the get :index into your setup or into a helper method if it only applies to some of your test cases.

