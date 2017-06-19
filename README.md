# Service Objects From Models

### The Problem
 Chances are, your model is doing too many things.  It is doing too many things if a model takes action that results in changes.  The problem with models taking action is that it leads to methods you generally don't need when you go to a model file, and therefore leads to bloated objects with functionality.  A second problem is that it often ties our models to other objects.

 ```ruby
class User < ActiveRecord::Base
  after_create :make_account

  def make_account
    Account.create(user: self)
  end
end
 ```

The above code couples our User model to the Account model, and it couples creating a new user to making a new account.  Be very skeptical of employing callback methods in models, and do not permit callback methods that call other models.

### C. Solving Large Models

Our models should **be something** but not **do something**.  This is part of a larger principle called *command query separation*.  Believe it or not, the model-view-controller pattern is one specific implementation of this broader command query principle, with controllers being responsible for commands and models being responsible for queries.  But sometimes, we as rails developers violate this principle.

1. Find out more about this problem by reading pages 23-34 of *[Clean Ruby](https://www.scribd.com/document/266755502/Jim-Gay-Clean-Ruby-pdf)*, and learn how to solve it.
2. You can also [learn more](https://www.saturnflyer.com/blog/4-simple-steps-extending-ruby-objects-the-tip-of-the-iceberg-with-dci) about DCI here.
3. And another example [emphasizing the code](http://blog.firsthand.ca/2011/10/rails-is-not-your-application.html) here
2. Then watch a [short video](https://www.youtube.com/watch?v=uIp6N89PH-c) reinforcing how this is solved in rails.


### D. Learn More

You can learn more about this problem by referencing the following resources:

* [Ruby Rogues episode on DCI](https://devchat.tv/ruby-rogues/211-rr-dci-with-jim-gay)
* [Command Query Principle Wikipedia Article](https://en.wikipedia.org/wiki/Command%E2%80%93query_separation)
* [Martin Fowler on the command query principle](https://martinfowler.com/bliki/CommandQuerySeparation.html)
* [DCI outside of ruby](http://www.artima.com/articles/dci_vision.html)

http://mikepackdev.com/blog_posts/24-the-right-way-to-code-dci-in-ruby
<p class='util--hide'>View <a href='https://learn.co/lessons/service-objects'>Service Objects</a> on Learn.co and start learning to code for free.</p>
