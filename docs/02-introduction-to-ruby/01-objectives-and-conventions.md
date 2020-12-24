---
title: Objectives & Conventions
parent: Introduction to Ruby
nav_order: 1
---

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
