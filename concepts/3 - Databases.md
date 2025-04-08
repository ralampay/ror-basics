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

Similary we can drop everything with:

```bash
rails db:drop
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

To save a record, we can call the `.save` method of an instance of our model. For example:

```ruby
student = Student.new
student.first_name = "John"
student.last_name = "Doe"
student.save
```

To query all records from a table, we can do:

```ruby
students = Student.all
```

To query a single record from a table, we can do:

```ruby
student = Student.find(1)
```

where `1` is the id of the student. Take note though that if student with id `1` is not found, Rails will throw an error. To instead return `nil` (no value), we can do:

```ruby
student = Student.find_by_id(1)
```

## Foreign Keys

To add a reference to an existing model, we can use the following `add_reference` method in a migration file:

```ruby
add_reference :table_name, :model, foreign_key: true
```

Take note that this follows the convention where it generates a suffixed `_id` field in the current model. 

We then modify both models to reference the one to many relationship using `belongs_to :model` and `has_many :pluralized_models`.

For example if `student belongs_to course` and `course has_many students`:

Migration file:

```ruby
add_reference(:students, :course, foreign_key: true)
```

In `app/models/student.rb`:

```ruby
belongs_to :course
```

In `app/models/course.rb`:

```ruby
has_many :students
```

Using these symbols will translate to a database query. For example:

```ruby
course = Course.find(1)
course.students
```

is the same as:

```ruby
students = Student.where(course_id: 1)
```
