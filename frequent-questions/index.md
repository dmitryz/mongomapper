---
layout: default
title: Frequent Questions
---

Frequent Questions
==================

What if none of these questions are my question?
------------------------------------------------

Everyone is pretty responsive on the [mailing list](http://groups.google.com/group/mongomapper) and you can also feel free to hop into \#mongomapper on irc.freenode.net.

Will MongoMapper use Active Model at some point?
------------------------------------------------

Yes. As of 0.9, Active Model is used.

What is the difference between a Document and an Embedded Document?
-------------------------------------------------------------------

A [Document](/documentation/document.html) is a top level entity that has its own collection. An [EmbeddedDocument](/documentation/embedded-document.html) is embedded inside of a Document. For example, in the document below, Template would be a MongoMapper::Document and would have a filename key. Field would be a MongoMapper::EmbeddedDocument and would be stored inside of the template document as an array of fields.

{% highlight javascript %}
{
  _id: ...
  filename: 'product',
  fields: [
    {_id: ..., key: 'description', type: 'long_text'},
    {_id: ..., key: 'weight', type: 'number'},
  ]
}
{% endhighlight %}

When should I embed?
--------------------

The general rule of thumb is to embed when the document will **only** be shown in the context of the parent document. If you need access to the document outside of the parent, don't embed. Instead de-normalize and store the document in two places.

What about Mongoid? Candy? MongoDoc? MongoModel?
------------------------------------------------

Different strokes for different folks. Read up on all of them and give them a try.