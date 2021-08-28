# Ownership

Ownership is a big part of why Rust is safe and doesn't need a garbage collector. Using ownership, Rust saves us time by catching mistakes in
memory allocation and deallocation at compile time rather than throwing a difficult to identify bug at runtime.

There are two ways Rust stores data in memory: stacks and heaps. Stacks are LIFO, fixed in size, easy and fast to copy. Heaps are random, size known only at runtime, difficult and slow to copy.
