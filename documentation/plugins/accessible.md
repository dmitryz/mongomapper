---
layout: documentation
title: Accessible
---

`attr_accessible` allows you to specify a whitelist of keys that can be set when using mass-assignment. It can be called multiple times, each call adds to the already declared attributes. The opposite of [`attr_protected`](/documentation/plugins/protected.html).

{% highlight ruby %}class User
  include MongoMapper::Document

  key :name, String
  key :email, String
  key :admin, Boolean

  attr_accessible :name, :email
end

user = User.new({
  :name => 'John',
  :email => 'john@doe.com',
  :admin => true
})
user.name # 'John'
user.email # 'john@doe.com'
user.admin # nil{% endhighlight %}