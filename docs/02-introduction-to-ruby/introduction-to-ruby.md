---
title: Introduction to Ruby
nav_order: 4
---

<!--prettier-ignore-start-->
#  Introduction to Ruby
{: .no_toc }

This module is an introduction to the Ruby programming language. It will also serve as a programming reference that you can use throughout the course.

This module will cover variable data types, boolean branching structures, looping structures and variable scope.

## Table of Contents
{: .no_toc .text-delta }  

1. TOC
{:toc}

<!--prettier-ignore-end-->

## Objectives

Upon completion of this module, you should be able to:

- Store data in variables and constants.
- Output strings to the screen with `puts`.
- Interpolate variables in strings.
- Understand the difference between strings and symbols.
- Use comments in your Ruby code.
- Define your own methods.
- Use blocks as method parameters.
- Store and retrieve single and multi-dimensional array data.
- Store and retrieve hash data.
- Code various conditional and looping structures.
- Understand the Ruby's scoping rules.

## Conventions

All source code in the notes will be syntax highlighted like so:

```ruby
ghost_quota = 37
if (caught_ghosts > ghost_quota)
  puts "You are done for the day."
else
  ghosts_required = ghost_quota - caught_ghosts
  puts "You need to find #{ghosts_required} more ghosts."
end
```

The output obtained by running the source through an interpreter will be displayed in a monospace font on a grey background:

```
You need to find 14 more ghosts.
```

## Ruby History

The Ruby programming language was created by a Japanese programmer, Yukihiro Matsumoto (known as "Matz" in the Ruby community). Matz started work on the language sometime in February 1993. The first alpha version was released in December 1994.

Matz main goal in developing Ruby was to create a scripting language that was more powerful than Perl, and more object oriented than Python.

The major guiding philosophy for the language has been "the principle of least surprise". Matz has often said that he is "trying to make Ruby natural, not simple," in a way that mirrors life.

#### Resources

- [About Ruby](http://www.ruby-lang.org/en/about/)
- [Perl Programming Language](http://en.wikipedia.org/wiki/Perl)
- [Pyton Programming Language](http://en.wikipedia.org/wiki/Python)
- [Matz' Blog](http://www.rubyist.net/~matz/) (In Japanese)

## Chunky Bacon

Try reading the following Ruby code out loud:

```ruby
4.times { puts "Chunky Bacon!" }
```

When executed by a Ruby interpreter the output is:

```
Chunky Bacon!
Chunky Bacon!
Chunky Bacon!
Chunky Bacon!
```

## Chunky Bacon in Java

Here is the same program written in Java.

```java
class ChunkyBacon {
    public static void main(String[] args) {
        for (int i = 0; i < 4; i++) {
            System.out.println("Chunky Bacon!");
        }
    }
}
```

When compared to Ruby, the Java version has some extra baggage:

- A ChunkBacon class required to wrap the entire program.
- A `public static void main(String[] args)` method required to wrap the mainline.
- A verbose for loop instead of a concise iterator.
- `System.out.prinln` vs. `puts`
- Semicolon required as an instruction separator.

## Ruby is OO

Ruby is an Object-Oriented language. Everything you manipulate in Ruby is an object. This means that every bit of information and code can be given their own properties and actions. Object-oriented programming calls properties by the name _instance variables_ and actions are known as _methods_.

We've already seen that numbers are objects in Ruby. In the Chunky Bacon program we used the `times` method of a FixNum object. To determine the type of any object you can use the _class_ method.

```ruby
puts 2.class
```

Output:

```
FixNum
```

The parent class of all objects in Ruby is the Object class.

## Constants

You can also create constants in Ruby. A constant holds a value that you do not expect to change. Constant names must start with a capital letter.

Unlike other languages, Ruby allows you to change the values in constants by assigning a new value to them:

```ruby
NUMBER_OF_ARMS = 2
NUMBER_OF_ARMS = 1
```

However, you'll get a warning each time you do this:

```
warning: already initialized constant NUMBER_OF_ARMS
```

## Variables

Ruby can store your data in variables. Variables are named placeholders that can store numbers, strings, and other data. Any lowercase word is a variable in ruby. Variables may consist of letters, digits and underscores.

You reference the data stored in a variable by using the variable’s name. For example, to store a value of `-5` in a variable named `temperature_on_mars`, you assign that variable the value.

```ruby
temperature_on_mars = -5
puts temperature_on_mars * 2
```

On the second line of the above program we are outputting twice the value of the number stored in our variable.

## Strings

Strings are any sort of characters (letters, digits, punctuation) surrounded by quotes. Both single and double quotes are used to create strings.

```ruby
opening_line  = 'It was the best of times.'
movie_trailer = "In a land that time forgot, "
```

### Concatenation

We can add to a Strings by using the plus operator.

```ruby
opening_line   = opening_line + " It was the blurst of times."
movie_trailer += 'there grew a ninja '
movie_trailer += "who would never be forgotten."
```

#### Resources

- [String - RubyDocs](http://ruby-doc.org/core/classes/String.html)

## Expression Interpolation

Ruby performs expression interpolation on double-quoted strings using the `#{}` interpolation wrapper.

So instead of this:

```ruby
time = "4 o'clock"
state_of_town = "all is well"
town_crier = "It's " + time + " and " + state_of_town + "."
```

We can do this:

```ruby
town_crier = "It's #{time} and #{state_of_town}."
```

_Note: Expression interpolation will not work with single quoted strings._

## Numbers - Integers

The most basic type of number is an integer, a series of digits which can start with a plus or minus sign.

Commas are not allowed in numbers, but underscores are. If you choose, you can make large numbers more readable by marking your thousands with underscores.

```ruby
very_large_number  = 34_000_000_001
even_larger_number = very_large_number * 12_345
puts "Whoa #{even_larger_number} is a large number!"
```

Output:

```
Whoa 419730000012345 is a large number!
```

#### Resources

- [Fixnum - RubyDocs](http://ruby-doc.org/core/classes/Fixnum.html)
- [Bignum - RubyDocs](http://ruby-doc.org/core/classes/Bignum.html)

## Numbers - Floats

In Ruby decimal numbers are called floats. They consist of a number with a decimal place or a number that uses scientific notation.

```ruby
ALMOST_PI = 3.14
AVOGADROS_CONSTANT = 6.02214179e23
```

Note that both of these variables are constants because their names begin with a capital letter.

#### Resources

- [Float - RubyDocs](http://ruby-doc.org/core/classes/Float.html)

## Comments

In Ruby comments begin with the pound symbol (sometimes called a hash).

```ruby
# This is a Ruby comment
puts 'A comment follows this line.' # This is also a comment
```

Unlike Java, there are no multi-line comments in Ruby\*.

```java
/* This is a multi-line
comment in Java or C++.
Pretty slick, eh? */
```

In Ruby you would have to do this:

```ruby
# This is a multi-line
# comment in Ruby.
# Ya, sorta lame.
```

### Multi-line Comments in Ruby

Ruby actually does have multi-line comments, but I find them awkward to use. These comment block start with a `=begin` and end with a `=end`.

```ruby
=begin
This is a multi-
line comment in Ruby.
=end
```

The `=begin` and `=end` cannot be indented and must be the only text on that line.

## Expression Seperators

Using semicolons to terminate your expressions is optional in Ruby. Most Ruby code uses line ends to indicate the end of an expression or statement.

When a line ends in the middle of an expression, Ruby realizes that it will continue on the next line. For example, I can split x = 2 + 2 over two lines.

```ruby
x = 2 +
2
```

Ruby sees a single expression as it expects something after the +. If I wanted to put multiple statements on a line then I could use semicolons.

```ruby
x = 2 + 2; y = x + 1
```

In this course we'll try our best to avoid using semicolons.

## Arrays

An array is a list surrounded by square brackets and separated by commas. The data stored in an array can be retrieved using a zero-based index.

```ruby
numbers = [1, 2, 3] # Array of numbers
shopping_list = ['cake', 'chainsaw', 'slippers']
puts "I need a #{shopping_list[1]} post-haste."
```

Output:

```
I need a chainsaw post-haste.
```

There is a shortcut for building arrays of strings:

`%w[cake chainsaw slippers]` produces the same array as `shopping_list` array above without the need for quotes or commas.

_Warning:_ Avoid this shortcut if your strings contain spaces.

#### Resources

- [Array - RubyDocs](http://ruby-doc.org/core/classes/Array.html)

## More Arrays

Arrays can also be defined using the `new` method of the `Array` class. Double "less-than" symbols can be used to push data into an Array.

```ruby
a = Array.new
a << 'some' << 'things' << 'appended'
a[3] = '!'
puts a.join(' ')
```

Output:

```
some things appended !
```

#### Resources

- [Array#join](http://www.ruby-doc.org/core/classes/Array.html#M000294)

## Symbols

Symbols are words that look like variables. Just like variables they may contain letters, digits, or underscores. _But_, they must start with a colon.

```ruby
instructor = :kyle
random_care_bear = :funshine
```

Symbols are lightweight strings. Symbols are used extensively in the Rails framework in situations where you need a string but you likely won't be printing it to the screen.

#### Resources

- [Symbol - RubyDocs](http://ruby-doc.org/core/classes/Symbol.html)

## Hashes

A hash (sometimes called a map or a dictionary) is similar to an array. However, instead of storing and retrieving data using an index, hashes use key/value pairs.

Hash definitions use curly brackets instead of the square braces used to define arrays. Hashes can also be defined using the `new` method of the `Hash` class.

```ruby
zoo_count = { 'goats' => 14, 'zebras' => 12, 'robins' => 256 }
haberdashery = Hash.new
haberdashery['hats'] = 24 # Note we use square braces here.
puts "We have #{haberdashery['hats']} hats in stock."
puts "We have #{zoo_count['robins']} Robins in our zoo."
```

Output:

```
We have 24 hats in stock.
We have 256 Robins in our zoo.
```

Notice that the hash mappings are defined by way of a "`=>`", which is called a [Hash Rocket](http://www.flickr.com/photos/obie/1994393949/in/photostream/) for its _striking_ similarity to a [rocket ship laying on its side](http://www.flickr.com/photos/soraia23/2406286982/).

#### Resources

- [Hash - RubyDocs](http://ruby-doc.org/core/classes/Hash.html)

## Hashes and Symbols

It is very common to use symbols as hash keys instead of strings:

```ruby
zoo_animals = { :goats => 14, :zebras => 12, :robins => 256 }
puts "We have #{zoo_animals[:zebras]} Zebras in our zoo."
```

Output:

```
We have 12 Zebras in our zoo.
```

## Hashes and Symbols - New Style

Starting Ruby 1.9 we got a new way to define hashes that have symbol key.

Old Style:

```ruby
{ :username => 'bob',
  :password => 'pass123' }
```

New Style:

```ruby
{ username: 'bob',
  password: 'pass123' }
```

The `zoo_animals` has from the previous section could therefore be rewritten as:

```ruby
zoo_animals = { goats: 14, zebras: 12, robins: 256 }
puts "We have #{zoo_animals[:zebras]} Zebras in our zoo."
```

## Hashes of Hashes, Arrays of Arrays

Hashes can contain hashes. Arrays can contain arrays. Hashes can contain Arrays. Arrays can contain Hashes.

```ruby
# An Array of Hashes
two_day_forecast = [ { temp: 34, desc: 'sunny' },
                     { temp: 23, desc: 'light rain' }
                   ]
puts "Temp on the 2nd day: #{two_day_forecast[1][:temp]}"

# A Hash of Arrays
favourite_foods = { 'jane'  => ['cabbage','pizza'],
                    'john'  => ['rainbow trout', 'chalk']
                  }
jane_eats = favourite_foods['jane']
puts "Jane eats #{jane_eats[0]} and #{jane_eats[1]}."
```

### A Hash of Hashes

```ruby
config = {
  admin_user: { username: 'batman', password: 'foo'},
  tcp_config: { ip: '192.168.1.100', port: 80}
}
```

### An Mixed Bag

```ruby
container = [
  [3, 4],
  { 'dromedary' => 'one hump', 'camel' => 'two humps' },
  ['one','two', { friendly: true, shy: true} ]
]
```

## Ranges

A range is two values surrounded by parentheses and separated by an ellipsis (in the form of two or three dots).

```ruby
alphabet_soup = ('a'..'z')
alphabet_soup.each { |letter| print letter }
```

Output:

```
abcdefghijklmnopqrstuvwxyz
```

If three dots are used then the final item in the range is not included. Try this:

```ruby
(1...5).each { |x| puts x }
```

Do not confuse ranges with arrays. They are entirely different beasts. However, ranges can be converted to arrays using their `to_a` method:

```ruby
alphabet_array = alphabet_soup.to_a
```

#### Resources

- [Range - Rubydoc](http://ruby-doc.org/core/classes/Range.html)

## Methods

Methods do things, they are the verbs of computer programming.

In Ruby (unlike in Java) we can define methods that aren't explicitly held within a class.

```ruby
def say_goodnight(name)
  puts "Goodnight, #{name}."
end

say_goodnight('John Boy')
say_goodnight('Matz')
```

Output:

```
Goodnight, John Boy.
Goodnight, Matz.
```

## Method Return Values

All methods return data to their caller. Ruby returns the last evaluated expression in the method.

```ruby
def square(x)
  x * x
end

# Note that multiple parameters are separated by commas.
def share_pizza(pieces_left, people)
  if (pieces_left < people)
    "Sorry I don't have enough pizza."
  else
    "Let's share. Any leftovers go to the dog."
  end
end

puts square(5)
puts share_pizza(4, 3)
```

Output:

```
25
Let's share. Any leftovers go to the dog.
```

## Nil

In Ruby `nil` represents emptiness. This means that any variable that is `nil` contains no value. The variable exists, it isn't undefined, but it _is_ empty.

```ruby
if (clown_car == nil)
  puts 'Where are all the clowns?'
end
```

This code will error as clown_car is not defined.

## True and False

All variables in Ruby are `true`, unless they are set to `false` or `nil`. This includes empty strings or even the number zero.

```ruby
if (0)
  puts 'Zero is true!'
end

empty_string = ''

if (empty_string)
  puts 'An empty string is true!'
end
```

Output:

```
Zero is true!
An empty string is true!
```

## Boolean Expressions

A boolean expression is a mathematical expression that results in either `true` or `false`.

Boolean expressions can contain the following common operators (and more):

|      Symbol      | Meaning               |
| :--------------: | :-------------------- |
|        ==        | equal                 |
|        !=        | not equal             |
|        >         | greater than          |
|        <         | less than             |
|        >=        | greater than or equal |
|        <=        | less than or equal    |
|        &&        | Boolean 'and'         |
| &brvbar;&brvbar; | Boolean 'or'          |

Boolean expressions can also contain a single boolean variable.

Let's assume we have a boolean variable named `you_have_had_enough` which has already been set to either true or false:

```ruby
puts 'Enough Already' if you_have_had_enough
```

## If Statements

Ruby's if statements work like you would expect.

```ruby
if (x > 5) then
  puts 'Yo, x is larger than 5.'
end
```

The `then` and the parentheses are optional:

```ruby
if x > 5
  puts 'Yo, x is still larger than 5.'
end
```

`if` as a modifier:

```ruby
puts 'Great Scott!' if speed_of_delorean > 88
```

## If Else Statements

Else statements also work as expected:

```ruby
if (temperature < 0)
  clothing = 'snowsuit'
elsif (temperature < 25)
  clothing = 'pant suit'
else
  clothing = 'bathing suit'
end
```

Note that we use `elsif` and not `else if`.

## Unless Statements

The `unless` statement is the bizarro evil twin (the logical inverse) of `if`:

```ruby
unless x <= 5
  puts 'Yo, x is larger than 5'
else
  puts 'Sadly, x is less than or equal to 5.'
end
```

Unless can also be used as a trailing modifier:

```ruby
snow_fort = 'awesome home' unless temperature > 0
```

All `unless` statements can be replaced by an `if` statement and an exclamation mark 'not' modifier. However, this usually makes the expression harder to read for humans. (Robots on the other hand love the 'not' modifier.)

```ruby
if !(x <= 5) # Identical to 'unless x <= 5'
  puts 'Yo, x is larger than 5'
else
  puts 'Sadly, x is less than or equal to 5.'
end
```

Simplified:

```ruby
if x > 5
  puts 'Yo, x is larger than 5'
else
  puts 'Sadly, x is less than or equal to 5.'
end
```

## Case Statements

Case statements are similar to those in Java. The `number_of_chairs` variable is said to be the _target_ of the `case` statement.

```ruby
number_of_chairs = 4

case number_of_chairs
when 1
  puts 'Lonely with teardrops in my tea.'
when 2
  puts 'Tea for two.'
  puts 'Two for tea.'
when (3..10) # Comparing against a range.
  puts "It's a tea party!"
else
  puts 'I feel claustrophobic.'
end
```

_Note: Unlike Java we do not require `break`s after each `when` block._

## Case Statment With Expressions

The target of the `case` statement can be left-out:

```ruby
enlightenment = 42

case
when enlightenment > 60
  puts 'You are too hasty, grasshopper.'
when (enlightenment < 40 || enlightenment == nil)
  puts 'You are like the sloth, my friend. Diligence is key!'
when enlightenment == 42
  puts 'Hello, Enlightened One.'
else
  puts 'Yeah, not quite, pal. Maybe next time.'
end
```

#### Resources

- Example lovingly 'borrowed' from the [Humble Little Ruby Book](http://www.linuxinsight.com/files/humble_little_ruby_book.pdf).

## Blocks

Any code surrounded by curly braces is a block. With blocks, you can group a set of instructions together so that they can be passed around your program.

Some methods can take blocks as parameters:

```ruby
42.times { puts 'Forty Two' }
```

If your block is longer than one line it's common practice to replace the curly braces with `do` and `end`:

```ruby
42.times do
  puts 'Forty Two'
  puts 'Wiggle Wiggle'
end
```

## Block Arguments

Block arguments are a set of variables surrounded by pipe characters and separated by commas. They are used to pass data into a block.

Here is a block that takes two parameters and sums them:

```ruby
{ |x, y| x + y }
```

This could also have been written as:

```ruby
do |x, y|
   x + y
end
```

In a sense you can think of blocks as being unnamed methods.

## Traversing Arrays

In most cases we use looping structures to traverse arrays.

Here's an example of an array traversal **in Java**:

```java
String[] ghosts = {"Blinky", "Pinky", "Inky", "Clyde"};

for (int i = 0; i < ghosts.length; i++) {
  System.out.println(ghosts[i]);
}
```

#### Resources

- [Pacman Ghost Names](http://en.wikipedia.org/wiki/Pac-Man#Enemies)

## Each Loops

In Ruby we can iterate through our ghost names using the `each` method of the Array class.

```ruby
ghosts = %w[Blinky Pinky Inky Clyde]

ghosts.each do |ghost_name|
  puts ghost_name
end
```

Note that the `each` method takes a block as an argument. We could also have use a curly-brace style block:

```ruby
ghosts.each { |ghost_name| puts ghost_name }
```

## Indexed Each Loops

While traversing an array you may require access to the currently index position:

```ruby
ghosts = %w[Blinky Pinky Inky Clyde]

ghosts.each_index do |i|
  puts "#{i}: #{ghosts[i]}"
end
```

This isn't nearly as elegant as a plain `each` iterator, but gets the job done.

Output:

```
0: Blinky
1: Pinky
2: Inky
3: Clyde
```

## Traversing Hashes

Traversing a hash is similar to traversing an Array.

```ruby
ghost_dictionary = { 'Blinky' => 'Shadow',
                     'Pinky'  => 'Speedy',
                     'Inky'   => 'Bashful',
                     'Clyde'  => 'Pokey'    }

ghost_dictionary.each do | nickname, character |
  puts "#{nickname} also know as #{character}."
end
```

Note the use of white-space in the hash definition. This is for human readability.

Output:

```
Blinky also know as Shadow.
Pinky also know as Speedy.
Inky also know as Bashful.
Clyde also know as Pokey.
```

#### Resources

- [Pacman Ghost Characters and Nicknames](http://upload.wikimedia.org/wikipedia/en/5/51/Pacman_title_na.png)

## Scope

Scope defines where in a program a variable is accessible. Where ever a variable is not accessible by your program it is said to be "out of scope" or "outside the current scope."

From the Poignant Guide:

> _"Microscopes narrow and magnify your vision. Telescopes extend the range of your vision. In Ruby, scope refers to a field of vision inside methods and blocks."_

#### Resources

- [Why's (Poignant) Guide to Ruby](http://mislav.uniqpath.com/poignant-guide/)

## Scope and Methods

Variables can be passed into a method as arguments. But, methods cannot 'see' variables defined outside its scope.

Data can also be returned from a method. But, variables defined within a method are only accessible until the method ends.

```ruby
# How many legs are there in total if we have
# 'creature_count' number of 'creature's?
def leg_count creature, creature_count
  if creature == 'human'
    legs = 2 * creature_count
  elsif creature == 'spider'
    legs = 8 * creature_count
  else
    legs = 4 * creature_count
  end
  "#{legs} #{creature} legs in total."
end

puts leg_count 'spider', 4
puts legs # This variable should not be available in the current scope.
```

Output:

```
32 spider legs in total.
NameError: undefined local variable or method 'legs'
```

## Scope and Blocks

Unlike methods, blocks can 'see' and modify variables that are defined in their vicinity.

```ruby
fruit = 'dragon fruit' # Will I ever get to eat the dragon fruit?
double_fruit = fruit * 2

['apple','pear','banana'].each do |fruit|
  double_fruit = fruit * 2
  puts "I ate one #{fruit}."
end

puts "It's true I ate one #{fruit}." #The block is done, so what is our fruit?
puts "But the double fruit is #{double_fruit}!"
```

Output:

```
I ate one apple.
I ate one pear.
I ate one banana.
It's true I ate one dragon fruit.
But the double fruit is bananabanana!
```

## Resources

### Free Ruby EBooks

- [Why's Poignant Guide](http://mislav.uniqpath.com/poignant-guide/)
- [Humble Little Ruby Book](http://www.linuxinsight.com/files/humble_little_ruby_book.pdf)

### Ruby Tutorials

- [Ruby @ Codecademy](https://www.codecademy.com/learn/ruby)
- [Ruby in Twenty Minutes](http://www.ruby-lang.org/en/documentation/quickstart/)
- [Things That Newcomers to Ruby Should Know](http://www.cs.auckland.ac.nz/references/ruby/doc_bundle/Newcomers/ruby.html)

### Ruby Reference

- [Ruby-Doc.org](http://www.ruby-doc.org/)
- [Ruby Style Guide](https://github.com/bbatsov/ruby-style-guide) - Community Code Conventions for Rubyists
