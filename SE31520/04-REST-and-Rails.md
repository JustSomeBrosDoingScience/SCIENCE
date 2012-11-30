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


Pure Matching
-------------

```ruby
match 'path/:param' => controller#action
```

All routes are processed in order.


Respond to methods
------------------

```ruby
respond_to do |format|
    format.type(params)
end
```

Will try to use the URL format, if not it will use the accept header. See also `respond_with`.
