# Data Types
---
- Rust is statically typed — it must know the data type of the variable at compile time.
- Data types can be defined implicitly or explicitly.
- Implicit Definition: Rust can infer the data type from the type of the value assigned to the variable.
- Explicit Definition: We can tell the compiler about the data type of the variable during declaration.
- There are two primitive data types in Rust — Scalar and Compound.
- Scalar: Integers, Float, Boolean and Char (they store a single value)
- Compound: Array and Tuple (they store multiple values in a single variable)

## Integers
    - There are two subtypes of integer data type based on the number of bits occupied by the variable in memory — fixed-size and variable-size
    - Fixed integer types have a specific number of bits in their notation. The data type starts with a letter — `i` or `u` — and is followed by a number — 8, 16, 32, 64. The `i` or `u` denotes signed or unsigned, meaning the integer can have a sign. The number denotes the size of the integer in bits. Full list: `i8`, `i16`, `i32`, `i64`, `u8`, `u16`, `u32`, and `u64`.
    - Variable size integers are integers whose size depends on the machine architecture.
    - Since there are so many subtypes of integers, the programmer is responsible for choosing an appropriate data type based on the value the variable is going to hold.
    - Each signed variant can store numbers from -(2n - 1) to 2n - 1 - 1 inclusive, where n is the number of bits that variant uses. So an i8 can store numbers from -(27) to 27 - 1, which equals -128 to 127. Unsigned variants can store numbers from 0 to 2n - 1, so a u8 can store numbers from 0 to 28 - 1, which equals 0 to 255.
    - **Integer Overflow**: Let’s say you have a variable of type u8 that can hold values between 0 and 255. If you try to change the variable to a value outside of that range, such as 256, integer overflow will occur.

## Floating Point
    - Floating point variables are used to store numbers with a fractional part.
    - Like integers, there are two subtypes to denote the size — `f32` and `f64`. The 32-bit floating-point is called single precision and 64 is called double precision. The 64-bit floating-point has more bits to store the number.

## Boolean
    - Used to store true/false values

## Character
    - Used to store a single character value — a single alphabet, special character, or digit.
    - The value assigned to a char variable should be enclosed in single quotes `''`.
    - Rust’s char type is four bytes in size and represents a Unicode Scalar Value, which means it can represent a lot more than just ASCII. Accented letters; Chinese, Japanese, and Korean characters; emoji; and zero-width spaces are all valid char values in Rust.

## String
    - Used to store any sequence of characters
    - The value assigned to a string variable should be enclosed in double-quotes `""`.
    - The explicit definition uses the `&str` keyword.

## Arrays
    - Used to store any homogenous sequence of elements.
    - It is a compound variable and is used when we want to store a collection of values of the same data type in a single variable.
    - Values of an array are enclosed in square brackets `[]`.
    - Individual values of an array can be read by using `[index]`. Index starts from 0.
    - Arrays can be made mutable using the `mut` keyword.
    - An entire array can be printed using the debug trait `{:?}`.
    - Length of an array: `arr.len()`.
    - Slice is a portion of an array and refers to a subset of a contiguous memory location. Unlike an array, the size of the slice is unknown and depends on the index defined as the value. Ex: `let slice_arr:&[i32] = &arr[0..2]`. Here `0` is the starting index and is inclusive. `2` is the ending index and is exclusive so the slice will have two elements. Declaring a slice has two parts. The `&arr` is a pointer to the array's memory location and `[0..2]` is the slice length.

## Tuples
    - Unlike Arrays, Tuples can store a sequence of heterogeneous elements, meaning they can be of different data types.
    - Values of a tuple are enclosed in `()`.
    - Individual values of a tuple can be accessed using the dot notation and index. Ex `person_data.0`.
    - We can also destructure a tuple and store each of it's elements in variables using `()`. Ex: `let (x, y, z) = person_data`.

## Constants
    - Constants are values that are unchangeable through out the program's scope.
    - They can be defined in global or local scope, unlike variables that can be declared only in local scope.
    - Constants are not mutable.
    - Constant data types must be defined explicitly.
    - By convention, constants are named in SCREAMING_SNAKE_CASE.
    - Constants cannot be shadowed.
