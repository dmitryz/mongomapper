---
layout: documentation
title: Plugins
---

Plugins power MongoMapper from the ground up. Every piece of functionality is a plugin, making MongoMapper easily extendable. If you need some crazy functionality, just build it.

The Anatomy of a Plugin
-----------------------

A plugin, in MongoMapper terms, is simply a module that extends `ActiveSupport::Concern`.

{% highlight ruby %}
module ActsAsListFu
  extend ActiveSupport::Concern

  included do
    key :position, Integer, :default => 1
  end

  def self.reorder(ids)
    # reorder ids...
  end

  def move_to_top
    # move to top
  end
end
{% endhighlight %}

Once you have your plugin defined, you can use it by calling the `plugin` method in your model:

{% highlight ruby %}
class Item
  include MongoMapper::Document
  plugin ActsAsListFu
end
{% endhighlight %}

If you would like to use a plugin in all documents or embedded documents, call `plugin` on the `Document` or `EmbeddedDocument` module:

{% highlight ruby %}
MongoMapper::Document.plugin(ActsAsListFu)
MongoMapper::EmbeddedDocument.plugin(ActsAsListFu)
{% endhighlight %}