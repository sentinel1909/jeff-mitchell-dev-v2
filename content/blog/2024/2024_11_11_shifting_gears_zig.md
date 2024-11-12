+++
title = "Shifting Gears: Ten Minutes of Zig - Hello World"
description = "An article which provides an introduction to the Zig programming language by doing a Hello World program."
date = "2024-11-11"
authors = ["Jeff Mitchell"]
draft = false
[taxonomies]
categories = ["Beginner's Guides"]
tags = ["zig"]
+++

I'm changing gears.

Don't get me wrong, Rust is my first love, but there's value in playing the field. I'm going to spend some time with Zig. I'll try to do 10 minutes every day for awhile, at least until I can do something meaningful.

Why Zig all of a sudden?

Why not.

Zig bills itself as a modern day C. In fact, right now out of the box it's a drop in compiler for the C language. How cool is that?

An alterior motive in approaching something fresh is to force myself to just study the language itself for awhile. I'm normally in this all fired rush to "do something". Figured I'd try to change that and just focus on the journey.

I'm not going to spend time telling you how to get Zig installed, you can do that by following the guidance here: [Zig Programming Language](https://ziglang.org/)

Fire up your VS Code (at least that's what I'm going to assume you're using) and install the offical Zig Language extension. This will give you many niceties, including compiler warnings.

Alright, right to the money shot, here's a cliched "Hello World!" in Zig:

```zig
// main.zig

// dependencies
const std = @import("std");

// main function
pub fn main() void {
  std.debug.print("Hello, {s}!\n", .{"World"});
}
```

Alright, let's break this down:

- comments in zig are preceded by a //
- the standard library is not in scope by default, we bring it in with an `@import` statement and bind it to a `const` variable named `std`
- variables with the const keyword are immutable in Zig
  - if you want a variable to be immutable, use the `var` keyword
- we start a main function, and mark it as public with the `pub` keyword
  - the main function must always be marked pub, so that the Zig compiler knows you want this to be the entry point for your program
- we call the `print()` function from `std.debug` in the standard library, the `print()` function accepts a string for output, which can contain arguments
- arguments to `print()` are an anonymous array, using the `.{<value>}` syntax, any placeholders in the output string are filled by the values in the anonymous array, ordered in the same order

That's it!

To run this, from a command line within the project folder, type: `zig run main.zig`

You should be greated with, "Hello, World!" output to the console.

The [Zig Language Reference](https://ziglang.org/documentation/0.13.0/) is very readable, and will tell you a few more things related to this Hello, World! example. Thanks for reading and good luck in your own adventures with Zig. I will be writing more about it as I go along.