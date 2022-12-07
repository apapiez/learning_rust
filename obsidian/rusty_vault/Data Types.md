---
tags: concept variables data-types
---
Rust is statically typed: All [[Variables and Mutability|Variables]] have specific data types which the compiler must know about at complie time.

There are two ways to provide this information to the compiler - either structuring the programme in such a way that the compiler can _infer_ the intended datatype from the code, or by providing a type hint to the compiler.

```rust
let x = 32; //compiler infers unsigned 32 bit integer
let x:u64 = 32; //we've told the compiler we want a 64 bit unsigned integer
```

While the compiler's type inference is pretty good, it will not work whenever there are multiple datatypes which might fit the code it's trying to work with:
```rust
let x = "42".parse().expect("Not a number!");
```

```terminal
Couldn't automatically determine type of variable `x`. Please give it an explicit type.
```

Unless you're working with really simple situations, it's probably best to  provide typehints - I find that these make it easier to reason about the programme anyway.

## Scalar Types

Scalar types represent a single value. They are composed of integers, characters, floats and bools.
The integers can take on 6 different specific types as needed:

#### Integers
![[Pasted image 20221207144432.png]]
#### Floats
Floats are either 32 or 64 bit and the type hints are `f32` or `f64`

#### Booleans
Bools can be `true` or `false`

#### Characters
Characters are the most primitive alphabetic type. The type annotation is `char` _Note:_ Character literals are denoted with single quote e.g. `let c = 'Z'`


## Compound Types

Compound types wrap multiple values into one type. There are two primitive compound types: tuples and arrays.

---


#Tuples are the most generic way to group variables of different types into one type. Once declared, tuples have a fixed size. Optionally, we can type annotate a tuple:

```rust
let tup: (i32, f64, u8) = (500, 6.4, 1);
```

We can get the values back out of tuple either by pattern matching or by dot syntax:

```rust
let (x, y, z) = tup;

println!("The first element of tup is {first} and the second is {second}",first=x, second=tup.1); // The first element of tup is 500 and the second is 6.4
```

An empty tuple `()` is called the #unit and represents an empty value, similar to `null` or `None` in other languages.

---
#arrays are compound data types where every data type must be the same. Arrays are less powerful than #vectors but are a way of ensuring that data is allocated on the #stack rather than on the #heap.

Arrays are created using a similar syntax to tuples: using square brackets instead of parentheses:

```rust
let a: [i32; 5] = [1, 2, 3, 4, 6]; // we must give the type hint and size of the array to the compiler
```

Array elements can be accessed using indexing like in python:

```rust
println!("The second value of a is {x}",x=a[1]); //The second value of a is 2
```

