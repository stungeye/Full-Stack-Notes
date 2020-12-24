---
title: Booleans and Conditions
parent: Introduction to Ruby
nav_order: 5
---

<!--prettier-ignore-start-->
## Booleans and Conditions
{: .no_toc }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

<!--prettier-ignore-end-->

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

- Example lovingly 'borrowed' from the Humble Little Ruby Book. (See [Resources](08-scope-and-more-resources.html#resources).)
