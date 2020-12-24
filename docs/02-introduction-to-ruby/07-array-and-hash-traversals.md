---
title: Array and Hash Traversals
parent: Introduction to Ruby
nav_order: 7
---

<!--prettier-ignore-start-->
## Array and Hash Traversals 
{: .no_toc }

## Table of Contents
{: .no_toc .text-delta }

1. TOC
{:toc}

<!--prettier-ignore-end-->

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

- [Pacman](http://en.wikipedia.org/wiki/Pac-Man)

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
