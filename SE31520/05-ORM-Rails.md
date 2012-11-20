Object Relation Mapping and Rails
=================================

Why ORM?
--------

ORM Focues on business code over SQL, reduces the need for special data access object classes. It
also means different methods of persistance can be supported.

ORM framework can be more robuse and efficient than pure SQL (depending on the framework) and 
allows for more reusable code. However they can be unweildly.


ActiveRecord
------------

Class is the table, an object is a row and an attribute is a column.

Pluralised by default, this can be overridden.

The model's attributes are implicitly derived from the database schema.

ActiveRecord uses the following type mapping (db -> Ruby):
* int -> FixNum
* decimal -> BigDecimal
* date -> Date
* BLOB, BLOD and Text -> String
* double and float -> float
* char and varchar -> String
* time -> Time
* boolean -> 0, "f", "false", "", nil -> false

The primary key is, by default, `:id`. Composite primary keys are not supported.

CRUD
====

Create:
-------
```ruby
activeRecord.save

ActiveRecord.create(params)

ActiveRecord.new

ActiveRecord.new(params)

ActiveRecord.new do |u|
    u.foo = foo
end
```

ID automatically generated.


Update:
-------
```ruby
activeRecord.save
```
This still happens if attributes haven't changed. Can update without having got an item from the 
databse, so long as an item with the same id does exist.

```ruby
activeRecord.update_attributes(params)

ActivateRecord.update(id, params)

activeRecord.update_attribute(param)

ActivateRecord.update_all("update", "where")
```


save, save!, create, create!
----------------------------

* `save` returns true or false.
* `save!` throws an exception on failure.
* `create` returns the object created or nil on failure.
* `create!` returns the object created or throws exception on failure.

As a side note, `create` shouldn't have an id on fail.

