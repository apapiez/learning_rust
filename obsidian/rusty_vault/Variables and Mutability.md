---
tags: concept
---
All variables have specific datatypes (e.g. u32) - see [[Data Types]]

By default, variables are immutable - they cannot be changed once assigned:

```rust
let x:u32 = 23;

x = x+10;
```
![[Pasted image 20221207142521.png]]
We can use the keyword `mut` to either declare a variable as mutable at the time of assignment, or to adjust it to be mutable:
```rust
let x:u32 = 10;

let mut x:u32 = x;

x = x + 10;

println!("The value of x is {x}")
```
outputs:
```terminal
The value of x is 20
```

<h4 style="box-shadow: 2px 2px 2px 2px;">Constants</h4>
Constants are calculated at compile time (therefore cannot rely on variables in their calculation) and cannot be mutated:
```rust
const PI:f32 = 3.14159;
```
<h3 style="box-shadow: 2px 2px 2px 2px; ">Shadowing</h3>
Shadowing is effectivley overwriting a variable, by repeating the `let` expression. This allows us to re-use variable names:
```rust
let x:u32 = 10;

println!("The value of x is {x}"); //The value of x is 10

let x:u32 = x + 10;

println!("The value of x is {x}"); //The value of x is 20
```

