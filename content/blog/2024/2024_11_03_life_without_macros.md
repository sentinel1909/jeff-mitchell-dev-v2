+++
title = "Life without Macros"
description = "An article which provides a brief overview of how to do output without a macro."
date = "2024-11-03"
authors = ["Jeff Mitchell"]
draft = false
[taxonomies]
categories = ["Beginner's Guides"]
tags = ["I/O, macro free"]
+++

Today I asked myself a random question about Rust programming.

Do I always have to use the `println!` macro to write output to `stdout`?

The answer is no. You can use the `Write` trait from the standard library and output quite neatly without using a macro. Macros are a time saving convenience, but increasingly I'd like to not use them so that I understand a little better what's going on underneath the hood.

It's actually pretty simple to output to `stdout` and can be done in a one-liner. Let's take a look.

```rust

// dependencies
use std::io::{Result, stdout, Write};

// main function
fn main() -> Result<()> {
  let msg = "Hello, World!";
  stdout().write_all(msg.as_bytes());

  Ok(())
}
```
That's pretty much it. What's going on here

- we bring some things into scope from the standard library, namely the `Result<T, E>` type, the `stdout` function and `Write` trait
- we bind a string slice with a message to a variable named `msg`
- we use the `stdout()` function to give us a handle to `stdout` which enables output to our console
- we call the `write_all()` method, giving it as a parameter our message, the message is converted to bytes, as required by `write_all` 
- the main function returns a `Result<T, E>` type because the I/O operation could fail in any number of ways.

If we save this program as `main.rs` and then run it using the rust compiler, like this: `rustc main.rs` then the message, "Hello, World!" will be visible in the console.

Macros are convenient, but they obscure details that you might want to know. The `println!` macro does bring some overhead, and in trivial code like above it doesn't matter, but in a larger CLI program, writing to `stdout` manually might be something you need to do for performance reasons.

Exercises like this are a little silly, but you can learn a lot by asking yourself "what if" kinds of questions.

Thanks for reading! I hope this small little byte was useful to you. Yes, my humour is terrible...I'll show myself out.

## References

[The Rust Standard Library](https://doc.rust-lang.org/std/)
