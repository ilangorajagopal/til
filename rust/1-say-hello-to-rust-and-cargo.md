# Say hello to Rust and Cargo

I'm a Javascript developer. It's been my language of choice for over half a decade. 
Recently I realized that it's the only language I actively use and I'm so out of touch with Python that I don't remember any of it.

I didn't want to learn Python again but still something new, that I would enjoy learning and building things with. I chose Rust because I've been curious about it for a while,
so here goes. 

As I'm learning Rust, I'll try and compare it to Javascript because that's the mental model I already have. It's gonna be hard learning Rust because of how different it is from Javascript.
But with consistency I should be able to build something tangible in the first month. I hope.

I'm also numbering the files so they are not arranged alphabetically and don't make sense when there are a bunch of markdown files in here.

Starting where everyone starts while learning a new programming language - saying hello to Rust and Cargo.

```rust
# main.rs

fn main() {
    println!('Hello, World!');
}
```

Rust is a compiled language so it's already different from Javascript. Rust programs start with the `main()` function.

Similar to `npm` and `package.json`, Rust has a package manager called `cargo` and packages are tracked
in `Cargo.toml`. So let's say hello to Cargo as well.

```rust
# main.rs

fn main() {
    println!('Hello, Cargo');
}

# Cargo.toml
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2018"

[dependencies]
```

There are no dependencies here, yet. Cargo can create a toml file using the command `cargo new hello_cargo`.
It creates a cargo project, initializes a git repository and creates the toml file.

---
PS: I'm learning Rust with The Rust Programming Language book. It's available for free on the Rust website.
[https://doc.rust-lang.org/book/title-page.html](https://doc.rust-lang.org/book/title-page.html)