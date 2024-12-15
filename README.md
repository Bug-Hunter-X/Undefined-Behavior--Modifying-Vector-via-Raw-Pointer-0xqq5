# Undefined Behavior in Rust: Modifying Vector via Raw Pointer

This repository demonstrates a common pitfall in Rust: modifying a vector through a raw pointer after the vector's capacity has potentially changed. This results in undefined behavior.  The `bug.rs` file contains the problematic code, while `bugSolution.rs` provides a safe and correct alternative.

## Problem
The original code obtains a mutable raw pointer to the vector's data using `as_mut_ptr()`.  Then, it uses this pointer to modify the first element of the vector. If the vector's capacity changes (e.g., due to reallocation), the pointer becomes invalid, leading to undefined behavior. This can manifest in various ways, including crashes, data corruption, or seemingly unpredictable results.

## Solution
The solution uses safe Rust mechanisms. Rather than manipulating raw pointers, it directly accesses and modifies the vector's elements using safe indexing.