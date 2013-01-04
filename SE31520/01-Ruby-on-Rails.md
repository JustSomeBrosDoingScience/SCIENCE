Ruby on Rails
=============


Ruby
----
Ruby is a dynamically typed, pure object-orientated language. It's also something that most people
on SE31520 won't have used before.

It's dynamically typed nature means that test suites are a must.


Why Rails?
----------
Java EE is a steep learning curve, whilst Rails provides a fairly simple way of quickly building
internet-based applications.

Rails is CRUD-style:

* Create
* Read
* Update
* Delete

Later on in the course (particulary for RESTful web services) the reason this is important will 
become apparent and how these to align nicely with each other.

Rails is also nice as it fall within the 80% of the 80:20 rule; 80% of the time something like 
Rails if perfectly suitable for purpose. Only 20% of the time do you need something truely 
heavyweight like Java EE.

Rails has a very good development community, as does Ruby. This means there are a lot of resources
out there one can use for reference.

Rails also has a lot of resusable components available (Gems, plug-ins, etc.).


Rails Design Philospohy
-----------------------
Rails follow the Don't Repeat Yourself (DRY) philosophy. You should define things once and once 
only.

It also follows convention over configuration, therefore providing sensible defaults and code 
generation to follow the Model View Controller (MVC) design pattern.


Overview of the Rails Architecture
----------------------------------
TODO Image here.

Generic Multi-teir Architechture:
TODO Another image here.


Rails Applications
------------------

* `apps/` Contains the MVC generated code.
* `config/` Configuration files for things like databases and routes.
* `db/` Database descriptors. Includes migration files (allows the database to be changed without 
  too much pain).
* `doc/` Documentation.
* `lib/` Internal libraries (authors note: I think at least).
* `log/` Log files.
* `public/` Static content.
* `test/` Testing code.
* `vendor/` Plugins local to the application.
* `Gemfile` Defines all the gems used by the application. Note that if no version is specified then
  the latest version of the gem will be installed.
* `Rakefile` Ruby makefile.

It should be noted that Gems are system-wide and plugins are application specific.


Rails MVC
---------
Rails has a lot of conventions with it's code:

Actions related to the HTTP Request methods (i.e. REST).

Models are named as singular objects (e.g. User, Object, etc.).

Tables, views, and most other things are names as plurals (e.g. Users, Objects, etc.).

A top level controller, the application controller, provides common code to all other controllers
used in the rails application. All other controllers should extend this.


Rails Database Management
-------------------------
Rails has three different databases:

* Development
* Production
* Test

All three of these are self-contained.

You can add index to the databases via the migration files in the following way:

```ruby
add_index :token, field
```


Rails Layouts
-------------
The main application template is found in: `app/views/layouts/application.html.erb`.

The default CSS is found in: `?/scaffold.css.scss`. Rails uses SASS CSS, a more powerful varient of
CSS.

In `.erb` files there are several different tags for embedding ruby:

* `<%= ... %>` For embedded Ruby with a return value.
* `<% ... %>` For embedded Ruby with no return value, or where the return value shouldn't be printed.

Ruby tries to prevent cross-site request forgeries using: `<%= csrf_meta_tags %>`

Chris also mentioned HAML being better than `html.erb`.


Testing Rails
-------------
Ruby being a dynamically typed language, testing is essential. In fact test-driven development is
advised when programming Ruby.

Test fixtures set up the test data.

Functional Tests test controllers.

Integration Tests test controllers working along a sequence.

The scaffolder generates a lot of these tests for you.

Chris also mentiond RSpec and Cucumber as behaviour driven testing libraries.


Unit Tests in Rails
-------------------

```ruby
class UT extend ActiveSupport::TestCase
```

Run `rake test:units` to run in isolation. Be warned that this is slow as it loads the whole of the
rails framwork into memory to do this.


Functional Tests in Rails
-------------------------
Test correct behaviour rather than whether a method is doing what it should do. With rails this is
typically the HTTP Request and Response codes.


Required Versions
-----------------

* Ruby 1.9.3+
* Rails 3.2.8+


Reading List
------------
Agile Web Development with Rails.
