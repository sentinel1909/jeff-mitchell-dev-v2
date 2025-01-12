+++
title = "Down into the Depths"
description = "A article which starts to explore how to how to create a hex dumper in Rust."
date = "2024-11-01"
authors = ["Jeff Mitchell"]
draft = false
[taxonomies]
categories = ["Beginner's Guides"]
tags = ["file I/O, hexadecimal"]
+++

## Background

I've been doing a lot with Rust and web dev, both front and back, since doubling down on the language a couple of years ago. There are two months left in 2024 and it's time for a shift of gears.

For awhile I'm going to go low, like very low. This article by Tania Rascia served to inspire: [Understanding Bits, Bytes, and Numerical Bases](https://www.taniarascia.com/bits-bytes-bases-and-a-hex-dump-javascript/)

I recommend reading Tania's work before continuing. She provides probably the easiest to understand explanation I've ever read. Like seriously, it's really good.

## What are We Going to Make?

We're going to start making a Rust version of the hex dumper program that Tania creates in NodeJS. In this first piece, we're going to keep the goals very simple:

- read in the content of any file, given the file name from the user
- output the content of the file in hexadecimal
- output the total length of the data read, in bytes

Later, we'll look at embellishing the output to be more pretty. Perhaps, in the future, we'll even add a web based UI. For now, this thing will be a command line only application.

## The Code

For the impatient amongst you, here's the final code:

```rust
// src/main.rs

// dependencies
use std::env::args;
use std::fs::File;
use std::io::{Read, Result};

// main function
fn main() -> Result<()> {

    // get the file path from the command line arguments
    let args: Vec<String> = args().collect();
    let file_path = &args[1];

    // read the file into a buffer
    let mut file = File::open(file_path)?;
    let mut buffer = Vec::new();
    file.read_to_end(&mut buffer)?;

    // convert each byte entry to hexadecimal
    let hex_buffer: Vec<String> = buffer.iter().map(|byte| format!("{:02x}", byte)).collect();

    // output the buffer
    println!("Buffer contents (in hexadecimal): {:?}", hex_buffer);

    // output the length of the buffer
    println!("Buffer length: {} bytes", buffer.len());

    Ok(())
}
```

## Breaking it Down

Ok, let's break this down.

The program flows like this:

- takes the arguments received by the user, just using the tools from the Rust standard library, and puts them in a vector
- grabs the first argument from the args vector and binds it to a variable called `file_path`, this represents the file we want the contents of
  - we're sticking with the standard library here and not bringing in the `clap` crate, as our CLI needs are pretty trivial
- opens the file given the `file_name`; this actually gives us what's known as a file handle, something we can work with further
- creates an empty buffer to read the file contents into
  - the buffer will be a simple vector containing the byte representation of the file contents
- reads the contents into the buffer
- makes a new vector by converting the decimal representation of each byte entry into hexadecimal
  - given our `hex_buffer` is a vector, we can use an iterator combined with a map function to transform the decimal bytes into their hexidecimal representation
- outputs a message along with the file contents, with each byte shown as a hexadecimal number
- outputs a message stating the length of the buffer, which is the number of bytes read

That's it!

There's more work to do, but that's enough for this article.

## Conclusion

Thanks for reading, I hope this super simple introduction has helped improve your understanding of file I/O in Rust as well as how to convert the decimal representation of bytes into the corresponding hexadecimal representation.

## References

[The Rust Standard Library](https://doc.rust-lang.org/std/)
