# Check, Run, Build, Release

These are four commands that will be used frequently when programming with Rust.

## check

`cargo check` is used to quickly check if the program compiles without any errors

## run

`cargo run` is used to compile and run in one command. It creates a binary under `target/debug/`.

## build

`cargo build` creates an executable of the project. It pulls any required external packages (or crates as they're called in Rust), and creates a single executable file. It is an unoptimized version that is used for sharing and testing.

## build --release

`cargo build --release` creates an optimized executable which is intended for distribution. It creates the executable under `target/release`. 