There were some more things to do finish the guessing game. 

1. Compare two numbers:

This syntax is quite easy. It's like a switch case but for comparing numbers. Before we can use this though, I've to do this: `use std:cmp:Ordering;`.

```rust
match guess.cmp(&secret_number) {
    Ordering::Less => println!("Too small!"),
    Ordering::Greater => println!("Too big!"),
    Ordering::Equal => println!("You win!")
}
```

2. Type casting the user's string input to a number

At this stage the game is almost over, but it won't compile because `guess` is a string. To convert it to a number we do this:

```rust
let guess = guess.trim().parse().expect("Please input a number");
```
This will convert our guess into a number. Note that we're declaring the `guess` variable again. This is called shadowing in Rust and allows us to re-declare variables for use in some situations.

3. Giving the user multiple tries

If we guessed the wrong number, the program returns "Too big" or "Too small". It will not give us multiple tries to get it right. To do that we wrap part of our code in a loop.

```rust
loop {
    println!("Please input your guess: ");

    let mut guess = String::new();

    io::stdin()
        .read_line(&mut guess)
        .expect("Failed to read line");

    let guess:u32 = match guess.trim().parse() {
        Ok(num) => num,
        Err(_) => continue,
    };

    println!("You guessed: {}", guess);

    match guess.cmp(&secret_number) {
        Ordering::Less => println!("Too small!"),
        Ordering::Greater => println!("Too big!"),
        Ordering::Equal => {
            println!("You win!");
            break;
        },
    }
}
```

Apart from the loop there are a couple more changes. The previous code will crash the program if the user enters a non-numeric value. To fix that, we use the match expression and add branches to our typecasting statement.
The other change is, if the user picks the correct number the program stops execution and exits.
