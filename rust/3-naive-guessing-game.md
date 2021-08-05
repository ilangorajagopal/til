# Naive Guessing Game

Well, it's not really a game but this chapter introduces some important concepts.

 - Reading an input from user and storing it
 - Error handling
 - Generating a random number
 - Using crates

## Reading an input from user and storing it

```rust
use std::io;

fn main() {
    let mut guess = String::new();
    
    io::stdin()
        .read_line(&mut guess);
}
```

The above code will throw an error because the value returned by the last statement could be an error.
Rust will not compile if we don't handle the error. Which is amazing because I think forcing error handling during coding enforces that habit. It took me many months to get into that habit with Javascript. It's also much faster since I'm learning about practices quicker than I would in Javascript.

So to fix the error, we:

## Handling errors

```rust
use std::io;

fn main() {
    let mut guess = String::new();
    
    io::stdin()
        .read_line(&mut guess)
        .expect('Failed to read line');
}
```

## Generating a random number

So rust doesn't have a random number generator, apparently. So we pull in a crate that can generate a random number. To do that we
add the dependency to the toml file.

```rust
# Cargo.toml
...

[dependencies]
rand = "0.8.4"


# main.rs
use rand::Rng;

fn main() {
    ...
    
    let secret_number = rand::thread_rng().gen_range(1..101);
}
```

I don't understand this part very clearly. We're "using" `Rng` from `rand` (I think) but using it in the program is different `rand::thread_rng().gen_range(1..101);`.
I understand the `thread_rng().gen_range(1..101)` but it's part of `rand` and not `Rng`. I'm coming at this from a Javascript developer, so I'm very wrong in how I reason about this. Something to read about in detail.
