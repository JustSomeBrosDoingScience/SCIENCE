Support for REST in Rails
=========================

a.k.a. Routing.

```ruby
resources :controller
```

Will create a route for all REST/CRUD operations for that controller. Assuine the methods exists in
said controller.

Parameters are passed in as a hash table.

URL Based Routing
-----------------

* `url_for` provides `http://example.com/path` based navigation.
* `*_path` provides `/path` based navigation
* `*_url` provides `http://example.com/path` based navigation. I noted something about redirection.


