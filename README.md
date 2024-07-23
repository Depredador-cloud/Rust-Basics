# Rust-Basics
# Basic Guide for Rust Programming

Welcome to the basic guide for Rust programming! This guide will help you get started with Rust, including installation, common programming concepts, and some advanced features. You can find more detailed information in the books "The Rust Programming Language" and "Programming Rust."

## Table of Contents

1. [Introduction](#introduction)
2. [Getting Started](#getting-started)
3. [Common Programming Concepts](#common-programming-concepts)
4. [Ownership and Borrowing](#ownership-and-borrowing)
5. [Structs and Enums](#structs-and-enums)
6. [Error Handling](#error-handling)
7. [Advanced Features](#advanced-features)
8. [Resources](#resources)

## Introduction

Rust is a systems programming language that focuses on speed, memory safety, and parallelism. It eliminates common bugs that plague other languages, such as null pointer dereferencing and data races.

## Getting Started

### Installation

To install Rust, you need to use the `rustup` tool, which manages Rust versions and associated tools:

**Linux or macOS:**
```sh
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

**Windows:**
Download and run `rustup-init.exe` from [rustup.rs](https://rustup.rs/).

After installation, you can update Rust by running:
```sh
rustup update
```

### Hello, World!

Create a new directory for your project and navigate into it:
```sh
mkdir hello_world
cd hello_world
```

Create a new file named `main.rs` and add the following code:
```rust
fn main() {
    println!("Hello, world!");
}
```

Compile and run your program:
```sh
rustc main.rs
./main
```

### Using Cargo

Cargo is Rust's build system and package manager. To create a new project with Cargo, run:
```sh
cargo new hello_cargo
cd hello_cargo
```

Build and run your project:
```sh
cargo build
cargo run
```

## Common Programming Concepts

### Variables and Mutability

Variables in Rust are immutable by default. To make a variable mutable, use the `mut` keyword:
```rust
let mut x = 5;
x = 6;
```

### Data Types

Rust has several data types, including scalar types (integers, floating-point numbers, booleans, and characters) and compound types (tuples and arrays).

### Functions

Functions are defined using the `fn` keyword:
```rust
fn main() {
    println!("Hello, world!");
}
```

Functions can have parameters and return values:
```rust
fn add(a: i32, b: i32) -> i32 {
    a + b
}
```

### Control Flow

Rust provides `if`, `else if`, `else`, and `match` for control flow, as well as loops such as `loop`, `while`, and `for`.

## Ownership and Borrowing

Ownership is a key feature of Rust, ensuring memory safety without a garbage collector.

### Ownership Rules

1. Each value in Rust has a variable that's called its owner.
2. There can only be one owner at a time.
3. When the owner goes out of scope, the value is dropped.

### Borrowing

References allow you to refer to some value without taking ownership. Mutable references allow you to change the value referred to:
```rust
fn main() {
    let s1 = String::from("hello");
    let len = calculate_length(&s1);
    println!("The length of '{}' is {}.", s1, len);
}

fn calculate_length(s: &String) -> usize {
    s.len()
}
```

## Structs and Enums

### Structs

Structs are used to create custom data types:
```rust
struct User {
    username: String,
    email: String,
    sign_in_count: u64,
    active: bool,
}

let user1 = User {
    email: String::from("someone@example.com"),
    username: String::from("someusername123"),
    active: true,
    sign_in_count: 1,
};
```

### Enums

Enums allow you to define a type by enumerating its possible values:
```rust
enum Message {
    Quit,
    Move { x: i32, y: i32 },
    Write(String),
    ChangeColor(i32, i32, i32),
}
```

## Error Handling

Rust handles errors using the `Result` and `Option` types.

### The `Result` Type

`Result` is used for recoverable errors and has two variants: `Ok` and `Err`:
```rust
use std::fs::File;

fn main() {
    let f = File::open("hello.txt");

    let f = match f {
        Ok(file) => file,
        Err(error) => {
            panic!("Problem opening the file: {:?}", error)
        },
    };
}
```

### The `Option` Type

`Option` is used for values that can be absent. It has two variants: `Some` and `None`.

## Advanced Features

### Generics

Generics allow for code that works with multiple data types:
```rust
fn largest<T: PartialOrd>(list: &[T]) -> &T {
    let mut largest = &list[0];

    for item in list {
        if item > largest {
            largest = item;
        }
    }

    largest
}
```

### Traits

Traits are used to define shared behavior:
```rust
pub trait Summary {
    fn summarize(&self) -> String;
}
```

### Lifetimes

Lifetimes prevent dangling references and ensure memory safety:
```rust
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}
```

## Resources

- [The Rust Programming Language](https://doc.rust-lang.org/book/)
- [Rust by Example](https://doc.rust-lang.org/rust-by-example/)
- [Rust Standard Library](https://doc.rust-lang.org/std/)

This guide provides a basic overview to get you started with Rust. For more comprehensive information, refer to the provided resources and the books "The Rust Programming Language" and "Programming Rust."
