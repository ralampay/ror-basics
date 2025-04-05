# Setup our Database

By default, Rails uses a database engine called `sqlite`. You can use the following online app to view your database:

[https://sqliteviewer.app/](https://sqliteviewer.app/)

## Creating our database

Creates our database according to `config/database.yml`

```bash
rails db:create
```

## Migrating our database

Performs a migration from our `migration files` to the database.

```bash
rails db:migrate
```

We can rollback (disregard) the latest migration by issuing the command:

```bash
rails db:rollback
```

### Adding Columns

To add a column in a migration in a migration file, the `change` method put in the following:

```ruby
add_column(:table_name, :field_name, :date_type)
```

where `data_type` can be one of the following:

* `string`: Used for text data with a default length of 255 characters.
* `text`: Suitable for longer text data that may exceed the limitations of a string
* `integer`: Used for whole numbers without decimal points
* `float`: Represents floating point numbers
* `decimal`: Useful for storing decimal numbers with specified precision and scale
* `boolean`: Stores a boolean value (`true` or `false`)
* `date`: Represents a date value without time information
* `time`: Stores time values without date information
* `datetime`: Suitable for storing date and time values together
* `binary`: Storing binary data

## Removing Columns

To remove a column:

```ruby
remove_column :table_name, :field_name
```

## Interacting with Models

Tables are often mapped to Ruby models under `app/models`. We can interact with the database via these models. One way to test things out is via an interactive console which is activated using the command:

```bash
rails console
```

Each line in the console is Ruby code that can be interpretted. Although because we are interacting with a live database, any change here will affect the underlying data. If we want to simply test things out and roll back all the changes we made in the console, we can instead issue:

```bash
rails console --sandbox
```
