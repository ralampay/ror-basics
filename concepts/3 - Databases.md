# Setup our Database

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
