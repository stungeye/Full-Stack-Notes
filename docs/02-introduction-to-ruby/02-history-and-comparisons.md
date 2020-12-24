---
title: History and Comparisons
parent: Introduction to Ruby
nav_order: 2
---

<!--prettier-ignore-start-->
## History and Comparisons
{: .no_toc }

### Table of Contents
{: .no_toc }

1. TOC
{:toc}

<!--prettier-ignore-end-->

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
