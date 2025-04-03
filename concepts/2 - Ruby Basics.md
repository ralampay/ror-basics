# Ruby Basics

Ruby is a dynamic, open-source programming language with a focus on simplicity and productivity. It has an elegant syntax that is easy to read and write. Ruby is widely used for web development, automation, and scripting.

Ruby scripts are saved as `.rb` files and can be executed using the `ruby` interpretter:

```bash
ruby yourfile.rb
```

Mandatory hello world would look something like:

```ruby
# yourfile.rb
puts "Hello World!"
```

`puts` is what we refer to as a `method` or a routine that can be executed. In this case, the `puts` method prints something out to standard output. It's also worth noting that methods in Ruby do not require the `()` when invoking it. Therefore, the above code is syntatically the same as:

```ruby
# yourfile.rb
puts("Hello World!")
```

## Basic Syntax

### Variables

Variables in Ruby are dynamically typed, meaning you don't need to explicitly define their type.

```ruby
name = "Alice"                  # String variable
age = 25                        # Integer variable
is_student = true               # Boolean variable
data = { first_name: "John" }   # Hash
```

Everything in Ruby is an object, that is, it has attributes and methods accessible via the `.` notation.

#### Strings

Strings are a collection of characters and are enclosed by `" "`. You'll run into strings a lot (in programming in general). One common operation in strings is called `interpolation` where we insert a value (native Ruby code) within a string by using the `#{}` where Ruby code is interpolated in between the `{ }` symbols. For example:

```ruby
message = "Hello world!"

puts "The message is #{message}"
```

#### Hashes

A **hash** in Ruby is a collection of key-value pairs, similar to a dictionary in other programming languages. Keys in a hash can be of any data type, but the most commonly used types are **symbols** and **strings**.

##### Creating a Hash

**Using Symbols as Keys**

```ruby
hash_with_symbols = {
  name: "Alice",
  age: 25,
  city: "New York"
}

puts hash_with_symbols[:name]  # Output: Alice
```

In this example, `:name`, `:age`, and `:city` are symbols used as keys.

**Using Strings as Keys**

```ruby
hash_with_strings = {
  "name" => "Bob",
  "age" => 30,
  "city" => "Los Angeles"
}

puts hash_with_strings["name"]  # Output: Bob
```
Here, keys are strings instead of symbols.

**Fetching Values**

```ruby
puts hash_with_symbols[:age]    # Output: 25
puts hash_with_strings["city"]  # Output: Los Angeles
```

If you try to access a key that does not exist, Ruby will return `nil` unless you use the `fetch` method:

```ruby
puts hash_with_symbols.fetch(:country, "Not Found")  # Output: Not Found
```

**Differences Between Symbols and Strings as Keys**

1. **Symbols are immutable** – They are stored only once in memory, making them more efficient.
2. **Strings can be modified** – Strings are mutable, which means they take up more memory if used frequently as keys.
3. **Symbols are conventionally used for identifiers** – They are often used in Rails and other Ruby frameworks.

**Converting Between Symbols and Strings**

Convert string keys to symbols:

```ruby
hash_with_strings.transform_keys(&:to_sym)
```
Convert symbol keys to strings:

```ruby
hash_with_symbols.transform_keys(&:to_s)
```

Hashes in Ruby are flexible and can use either strings or symbols as keys. Symbols are generally preferred for identifiers due to their efficiency, but strings offer more flexibility in some cases.


### Loops

Loops in Ruby allow repetitive execution of code blocks. Here are some common loop structures:

#### While Loop

Executes a block of code as long as a given condition is true.

```ruby
count = 0
while count < 5
  puts "Count: #{count}"
  count += 1
end
```

#### For Loop

Iterates over a range or collection.

```ruby
(1..5).each do |num|
  puts "Number: #{num}"
end
```

### Conditions

Conditional statements control the flow of execution based on boolean expressions.

```ruby
x = 10
y = 20

if x > y
  puts "x is greater than y"
elsif x < y
  puts "x is less than y"
else
  puts "x is equal to y"
end
```

## Methods and Blocks

### Defining a Method

Methods in Ruby are defined using the `def` keyword. They help in reusing code and making programs modular.

```ruby
def greet(name)
  puts "Hello, #{name}!"
end

greet("Alice")

# or

greet "Alice"
```

Arguments in methods can also be named with a default value (optional):

```ruby
def greet(first_name: "John", last_name:)
  puts "#{first_name} #{last_name}"
end

greet(last_name: "Doe")
```

### Blocks
A block is a piece of code enclosed between `do...end` or `{...}` that can be passed to methods.

#### Using a Block with `yield`
```ruby
# Block using do-end
def repeat(times)
  times.times do
    yield
  end
end

repeat(3) { puts "Hello!" }
```

## Symbols
A symbol is a lightweight, immutable identifier often used as keys in hashes.
```ruby
:name_symbol = :alice
puts :alice.object_id == :alice.object_id # True, symbols are immutable and unique
```

## Classes and Objects
Ruby is an object-oriented language, and everything in Ruby is an object. You can define your own classes to create objects with attributes and behaviors.

### Defining a Class
A class in Ruby is a blueprint for creating objects. It defines properties (instance variables) and methods.
```ruby
class Person
  attr_accessor :name, :age
  
  def initialize(name, age)
    @name = name
    @age = age
  end
  
  def introduce
    puts "Hi, my name is #{@name} and I am #{@age} years old."
  end
end

# Creating an instance of the class
person = Person.new("Alice", 25)
person.introduce
```

### Explanation

- `attr_accessor` automatically generates getter and setter methods for instance variables.
- The `initialize` method is a constructor that runs when an object is created.
- Instance variables, prefixed with `@`, store object-specific data.
- Methods define the behaviors of an object.

### Best Practices

- Use `attr_reader` to only expose the members of a class

## Ruby Pass by Reference by Value

Ruby is **pass-by-value**, but with a twist: it passes references **by value**. This is often referred to as **pass-by-reference-value**.

## Explanation:

- When you pass an object to a method, Ruby passes a **reference** to that object, but the reference itself is passed **by value**.
- This means that within the method, you can **modify the object's state** (if it's mutable), but you **cannot change the original reference** to point to a new object.

## Example 1: Modifying an Object (Mutable Objects)

```ruby
def modify_string(str)
  str << " World"  # Modifies the original object
end

s = "Hello"
modify_string(s)
puts s  # Output: "Hello World"
```

Since `s` is a reference to a mutable `String` object, modifying it inside the method affects the original object.

## Example 2: Assigning a New Object

```ruby
def reassign_string(str)
  str = "New String"  # This changes the local reference, not the original object
end

s = "Hello"
reassign_string(s)
puts s  # Output: "Hello"
```

Here, `str = "New String"` only changes the local reference inside the method; `s` remains unchanged outside.

## Example 3: Immutable Objects

```ruby
def modify_number(n)
  n += 1  # Creates a new object, does not modify original
end

x = 5
modify_number(x)
puts x  # Output: 5
```

Since integers are immutable, `n += 1` creates a **new** `Integer` object rather than modifying `x`.

## Summary:
- **Mutable objects (e.g., arrays, hashes, strings) can be modified inside a method.**
- **Reassigning a variable inside a method does not affect the original reference outside the method.**
- **Immutable objects (e.g., numbers, symbols) cannot be modified.**

So, while Ruby technically passes references **by value**, the behavior depends on whether the object is mutable or not.

## Guided Exercise

1. Install the gem `httparty`

```bash
gem install httparty
```

2. [https://official-joke-api.appspot.com/jokes/programming/random](https://official-joke-api.appspot.com/jokes/programming/random)
