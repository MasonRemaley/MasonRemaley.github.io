---
layout: page
excerpt_separator: <!--more-->
order: 0
---

I wrote a scripting language in [Rust](https://www.rust-lang.org){:target="_blank"} that I use for all my [game dev projects](/projects/way-of-rhea).

It's statically typed but with type inference, has an incremental garbage collector, and compiles down to a bytecode I wrote so that it can be executed by a virtual machine I also wrote in Rust. This makes it super easy to hot swap out scripts in game without reloading the whole game, and also made it pretty easy to set up a read eval print loop. I'm not ready to release it publicly yet, but here's a few snippets to show it off:

```rs
use dbg;

fn main() {
    dbg::println("Hello, world!");
}
```

<!--more-->

It's expression based, if/else statements for example result in values that can be stored in variables or returned:
```rs
fn factorial(n: int) -> int {
    if n > 1 {
        n * factorial(n - 1)
    } else {
        n
    }
}
```

It's easy to interface with the language from Rust:
```rs
// Define a Rust marker type for a type that will be defined in a script
// so that we can pass it to Rust.
script_struct!(math::Point<T>);

fn main() {
    // Create a new virtual machine to run the code in
    let mut vm = Vm::new();

    // Compile the geometry module from source
    vm.load_string("geom", r"
        pub struct Point::<T> {
            pub x: T,
            pub y: T,
        }
    ").unwrap();

    // Create an instance of `Point` in the script and pass it to Rust
    let origin: Managed<Point<Ratio>> =
        vm.repl("@Point::<ratio> { x: int, y: int }")
          .unwrap().downcast(&vm).unwrap();

    // ...now we're free to store the point, pass it back into other functions
    // defined in the script, etc
}
```

And much more...
```rs
use dbg::println;

struct Vec2 {
    x: ratio,
    y: ratio,
}

// These vecs are passed in as immutable garbage collected references
fn dot(a: @Vec2, b: @Vec2) -> ratio {
    a.x * b.x + a.y * b.y
}

// On the other hand, this vec is passed in as a mutable garbage collected
// reference
fn scale(v: @mut Vec2, s: ratio) {
    a.x * b.x + a.y * b.y
}

fn main() {
    let a = @mut Vec2 { x: 1.0, y: 2.0 };
    let b = @mut Vec2 { x: 3.0, y: 4.0 };

    let dot = dot(a, b); // If not specified, the types of locals are inferred
    scale(a, dot);

    // Support for sum types!
    print_option_i32(Option::Some::<i32>(10));
}

enum Option::<T> {
    Some(T),
    None,
}

fn print_option_i32(n: Option::<i32>) {
    match n {
        Some(x) => println(f"The value is {x}!"),
        None => println("no value :("),
    }
}
```
