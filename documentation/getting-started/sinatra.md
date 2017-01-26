---
layout: documentation
title: Installation in Sinatra
---

First, add MongoMapper to your `Gemfile`, and run `bundle install`:

{% highlight ruby %}
gem 'mongo_mapper'
gem 'bson_ext'
{% endhighlight %}

If you're not using `Bundler.require` in the top of your Sinatra application then you'll need to require the MongoMapper library:

{% highlight ruby %}
require 'mongo_mapper'
{% endhighlight %}

You'll also need to set up your MongoDB connection in your `configure` method call. If you have a MongoDB URI for the database connection (i.e. on [Heroku](http://heroku.com)):

{% highlight ruby %}
configure do
  MongoMapper.setup({'production' => {'uri' => ENV['MONGODB_URI']}}, 'production')
end
{% endhighlight %}

You can now define your models and start using MongoMapper in Sinatra!