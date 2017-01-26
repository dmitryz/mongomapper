---
layout: documentation
title: EmbeddedDocument
---

Embedded documents are almost identical to [Documents](/documentation/document.html) with one exception: they are saved inside of another document instead of in their own collection. For example, lets say we have orders and orders have line items.

{% highlight ruby %}
class Order
  include MongoMapper::Document
  many :line_items
  timestamps!
end

class LineItem
  include MongoMapper::EmbeddedDocument

  key :name, String
  key :quantity, Integer
end

Order.create(:line_items => [
  LineItem.new(:name => 'Undershirt', :quantity => 5),
  LineItem.new(:name => 'Underwear',  :quantity => 5),
  LineItem.new(:name => 'Socks',      :quantity => 3),
])
{% endhighlight %}

By including EmbeddedDocument instead of Document, MongoMapper knows to store the line items inside of the orders. In Mongo, this would create a collection named orders with one document that contained 3 line items. Below is what the document would look like represented in Ruby.

{% highlight ruby %}{
  "_id"=>BSON::ObjectId('4d39d708bcd1b368fc000004'),
  "created_at"=>Fri Jan 21 18:57:12 UTC 2011,
  "updated_at"=>Fri Jan 21 18:57:12 UTC 2011,
  "line_items"=> [
    {"name"=>"Undershirt", "quantity"=>5, "_id"=>BSON::ObjectId('4d39d708bcd1b368fc000001')},
    {"name"=>"Underwear", "quantity"=>5, "_id"=>BSON::ObjectId('4d39d708bcd1b368fc000002')},
    {"name"=>"Socks", "quantity"=>3, "_id"=>BSON::ObjectId('4d39d708bcd1b368fc000003')}
  ]
}{% endhighlight %}