---
layout: documentation
title: Protected
---

`attr_protected` allows you to specify a list of keys that cannot be set when using mass-assignment. It can be called multiple times, each call adds to the already declared attributes. It is recommended that you specify [`attr_accessible`](/documentation/plugins/accessible.html) instead of `attr_protected`.

{% highlight ruby %}
class User
  include MongoMapper::Document

  key :name, String
  key :email, String
  key :admin, Boolean

  attr_protected :admin
end

user = User.new({
  :name => 'John',
  :email => 'john@doe.com',
  :admin => true
})
user.name   # 'John'
user.email  # 'john@doe.com'
user.admin  # nil
{% endhighlight %}