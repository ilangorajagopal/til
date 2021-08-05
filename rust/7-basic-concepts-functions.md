# Functions
---
Functions in Rust are like functions in any other language. Rust programs so far already start with the `main()` function. So writing new functions is not new.

There were some things to look out for, however.

## Parameters/Arguments

Parameters is the correct term but is often used interchangeably with arguments. Types of function parameters have to be declared during function definition.

```rust
fn another_function(x:i32) {
    println!("The value of x is {}", x);
}
```

## Expressions vs Statements

The terms are interchangeable in other language but in Rust there is a clear distinction. 

Statements are instructions that perform some action and don't return a value. Expressions evaluate to something and return a value.

Example:

`let y = 6;` is a statement. It doesn't return a value. Which is different in some languages where variable declaration returns the value of the variable.

```rust
let y = {
    let x = 3;
    x + 1
};
```

The `x + 1` is an expression. It returns 4 which is then bound to `y`. Expressions do not include semicolon. If we add a semicolon to an expression it becomes a statement. In the above example,
if we add a semicolon to `x + 1`, the compiler throws an error.

## Return values

Functions can return values like in other languages. But we have to specify the type of the return value in the function definition.

```rust
fn five() -> i32 {
    5
}
```

Notice that the lone `5` is an expression. That value is returned when the function is called. If we add a semicolon after `5`, the compiler throws a type mismatch error because we specified 
that the return value would be `i32`.