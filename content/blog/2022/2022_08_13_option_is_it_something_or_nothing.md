+++
title = "Is it Something or Nothing: The Option Type"
description = "An introduction to Rust's Option type."
date = "2022-09-13"
updated = "2025-01-02"
[taxonomies]
categories = ["Intermediate Guides"]
tags = ["rust", "enums", "option"]
+++

There's a saying that null values were a "billion dollar mistake". Search history, you'll quickly find the evidence of the havoc of "nothing". Nothing values are notorious, but somehow necessary. How exactly do we represent a thing that might be nothing?

How indeed.

Riddles and existential arguments aside, let's take a look at how the Rust language chooses to represent something...that might actually be nothing.

In an [earlier article](@/blog/2022/2022_05_21_bigger_building_blocks_intro_to_enumerations.md), I introduced the notion of enumerations, or enums, that are useful to represent types in Rust. You’ll also recall that Enums can optionally contain data. It’s time to introduce one of two special Rust enums…the Option type. Today I give you a short bite on this topic.

An Option can contain something and or it can contain nothing. It’s a little like Schrödinger's Cat, it might be alive (contains something) or it might be dead (contains nothing) and you don’t know until you check. Let’s dive in.

An Option looks like this:

```rust
enum Option<T> {
	None,
	Some(T),
}
```

The None variant is used when the option holds nothing, no data. The Some variant can contain something. The <T> is the notation for a generic type parameter. I haven’t covered generics yet, but their nuts and bolts are not super important for this discussion. In the context of the Option enum, it means a data type of any kind. It could, for example, contain a single integer.

The Option enum provides a graceful way to implement a null value. The notion of a null value has wreaked havoc on the computing world, to say the least.

This Option concept is best illustrated with an example. Consider this program which takes two numbers, tries to divide them, and provides the result:

```rust
function divide(numerator: f64, denominator: f64) -> Option<f64> {

	if denominator == 0 {
		None
	} else {
		Some(numerator/denominator)
	}
}

fn main() {

	let numerator = 10.0;
	let denominator = 0.0;

	let result = divide(10.0, 0.0);

	match result {
		Some(x) => println!("Result: {}", x),
		None => println!("Sorry, cannot divide by 0"),
        }
}
```

This program has a main function and a function called divide. In the main function, we declare two floating point numbers as the numerator and denominator variables, then we pass them to the divide function and assign the answer to the variable result. The divide function accepts two floating point parameters, the numerator and the denominator. It returns an option, which will either be a floating point number or nothing. The function checks if the denominator is zero, if it is, our returned option is assigned None as its value. If the denominator is non-zero, our math can proceed and our option will return the calculation result.

Back inside the main program, with the result in hand, we run a match expression on it and output the answer. If our option contains something we output the result of the calculation. If our option contains nothing, we output a message stating that you can’t divide by zero.

The option type is almost always combined with a match expression for further processing.

Option is a flexible and versatile construct in the Rust language. It is often used for:

- initial values
- optional function arguments
- swapping things out of difficult situations
- basic error handling, where None is returned and perhaps combined with a message to represent the error

The Rust standard library documentation has a good in-depth description of the option type. I recommend you read it for the full scoop.

In a future article, I’ll go through the Result type, which is the second special enum type built into the Rust language. Thanks for reading!

References:
[The Rust Programming Language, Chapter 6.1, Defining an Enum](https://doc.rust-lang.org/book/ch06-01-defining-an-enum.html)
