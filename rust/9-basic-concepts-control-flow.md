# Control Flow
---
Similar to functions, control flow is similar to other languages. But there are differences.

## Condition must evaluate to boolean

This is different from Javascript where `if (5)` returns true. In Rust, `if 5` throws an error because the condition is not boolean. Rust doesn't type-cast conditions automatically.

## Using `if` in a `let` statement

This is valid in Rust: `let number = if condition { 5 } else { 6 };`. Note that the `if` and `else` blocks have expressions, so they return a value. 
If the `if` and `else` blocks return values of different types, the compiler will throw an error.  

## Loops

Same as other languages for the most part. Returning values from a `loop` is done by specifying the value after a `break`. When the loop breaks, it returns this value, which can then be stored in a variable.

```rust
let result = loop {
    counter += 1;

    if counter == 10 {
        break counter * 2;
    }
};
```

### `while`

```rust
let mut number = 3;

while number != 0 {
    println!("{}!", number);

    number -= 1;
}
```

### `for`

It's safer to use `for` when looping arrays because `while` may sometimes cause panic when the index length is incorrect.

```rust
let a = [10, 20, 30, 40, 50];

for element in a.iter() {
    println!("the value is: {}", element);
}
```

`for`, apparently, is the default loop used by Rust programmers even when not using arrays. A `Range` is used instead:

```rust
for number in (1..4).rev() {
    println!("{}!", number);
}
```
