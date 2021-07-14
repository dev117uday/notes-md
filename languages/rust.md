---
description: Aamzing programming lanuguage but ...
---

# Rust

## Rust

### Concepts of Rust

#### Ownership

All programs have to manage the way they use a computer’s memory while running. Some languages have garbage collection that constantly looks for no longer used memory as the program runs; in other languages, the programmer must explicitly allocate and free the memory. Rust uses a third approach: memory is managed through a system of ownership with a set of rules that the compiler checks at compile time. None of the ownership features slow down your program while it’s running.

[Read here for proper info](https://doc.rust-lang.org/book/ch04-01-what-is-ownership.html)

Keep these rules in mind as we work through the examples that illustrate them:

1. Each value in Rust has a variable that’s called its owner.
2. There can only be one owner at a time.
3. When the owner goes out of scope, the value will be dropped.

#### Traits in Rust Programming

A trait tells the Rust compiler about functionality a particular type has and can share with other types. We can use traits to define shared behavior in an abstract way. We can use trait bounds to specify that a generic can be any type that has certain behavior.

#### Traits in Rust Programming

A trait tells the Rust compiler about functionality a particular type has and can share with other types. We can use traits to define shared behavior in an abstract way. We can use trait bounds to specify that a generic can be any type that has certain behavior.

## Formating Strings

### The Basic Formatting

#### Single Placeholder

```rust
fn main() {
    println!("Number: {}", 1);
}
```

#### Multiple Placeholders

```rust
fn main() {
    println!("{} is a {} company", "Educative", "Software");
}
```

#### Positional Arguments

```rust
fn main() {
    println!("Enhance your coding skills from {0} courses.  {0} courses are very {1}", "Educative", "interactive");
}
```

#### Named Arguments

```rust
fn main() {
    println!("{company} provides {kind} courses", company = "Educative", kind = "interactive");
}
```

#### Placeholder Traits

```rust
fn main() {
    println!("Number : 10 \nBinary:{:b} Hexadecimal:{:x} Octal:{:o}", 10, 10, 10);
}
```

#### Placeholder for a Debug Trait

```rust
fn main() {
    println!("{:?}", ("This is a Rust Course", 101));
}
```

#### `print!()` && `println!()`

```rust
fn main() {
    print!("Rust Programming");
    print!(" Course");
}
```

```rust
fn main() {
    println!("Rust Programming");
    println!("Course");
}
```

#### `eprint!()`&& `eprintln!()`

```rust
fn main() {
    eprint!("Rust Programming");
    eprint!(" Course");
}
```

```rust
fn main() {
    eprintln!("Rust Programming");
    eprintln!("Course");
}
```

## Concept of Lifetime

### Lifetimes Specifiers

**Note : Please read the whole note in order to revise it properly**

Every reference in Rust has a lifetime, which is the scope for which that reference is valid.

#### Preventing Dangling References with Lifetimes :

The main aim of lifetimes is to prevent dangling references, which cause a program to reference data other than the data it’s intended to reference.

```rust
{
    let r;
    {
        let x = 5;
        r = &x;        // reference to x    
    } 
    // 'r' goes out-of-scope here
    println!("r: {}", r);   // ERROR
}
```

**Error message by compiler**

```rust
  --> src/main.rs:7:17
   |
7  |             r = &x;
   |                 ^^ borrowed value does not live long enough
8  |         }
   |         - `x` dropped here while still borrowed
9  | 
10 |         println!("r: {}", r);
   |                           - borrow later used here

error: aborting due to previous error

For more information about this error, try `rustc --explain E0597`.
error: could not compile `lifetime.rs`.

To learn more, run the command again with --verbose.
```

#### The Borrow Checker :

The Rust compiler has a borrow checker that compares scopes to determine whether all borrows are valid.

```rust
 {
    let r;                  // ---------+-- 'a
    {                         //          |
        let x = 5;            // -+-- 'b  |
        r = &x;               //  |       |
    }                       // -+       |
    println!("r: {}", r);   //          |
}
```

Here, x has the lifetime `'b`, which in this case is larger than `'a`. This means r can reference x because Rust knows that the reference in r will always be valid while x is valid.

Generic Lifetimes in Functions :

Generic means `characteristic of or relating to a class or group of things; not specific.`

A **generic lifetime parameter** imposes a **lifetime constraint** on the reference\(s\) and the return value\(s\) of a function. While compiling the code, a **generic lifetime** is substituted for a `concrete lifetime`, **which is equal to the smaller of the passed references' lifetimes.** **\(super important\)**

Consider the following peice of code :

```rust
fn main() {
    let string1 = String::from("abcd");
    let string2 = "xyz";

    let result = longest(string1.as_str(), string2);
    println!("The longest string is {}", result);
}
fn longest(x: &str, y: &str) -> &str {        
//error: &str is a reference string, you need to define it's lifetime.
    if x.len() > y.len() {
        x
    } else {
        y
    }
}
```

We get an error :

```rust
error[E0106]: missing lifetime specifier
 --> src/main.rs:9:33
  |
9 | fn longest(x: &str, y: &str) -> &str {
  |                                 ^ expected lifetime parameter
  |
  = help: this function's return type contains a borrowed value, but the signature does not say whether it is borrowed from `x` or `y`

error: aborting due to previous error

For more information about this error, try `rustc --explain E0106`.

To learn more, run the command again with --verbose.
```

#### Lifetime Annotation

* Lifetime Annotation don’t change how long any of the references live.
* Lifetime Annotation describe the relationships of the lifetimes of multiple references to each other without affecting the lifetimes

**Example Syntax:**

```rust
&i32        
// a reference
&'a i32     
// a reference with an explicit lifetime
&'a mut i32 
// a mutable reference with an explicit lifetime
```

Let’s say we have a function with the parameter first that is a reference to an i32 with lifetime `'a`. The function also has another parameter named second that is another reference to an i32 that has the lifetime `'b`. The lifetime annotations indicate that the references first and second must both live as long as that **generic lifetime**, or the lifetime of the shortest, known as concrete lifetime.

#### Lifetime Annotations in Function Signatures

Let's go back to our longest function and solve the error

```rust
fn longest<'a>(x: &'a str, y: &'a str) -> &'a str {
    if x.len() > y.len() {
        x
    } else {
        y
    }
}
```

Here :

* In `fn longest<'a\>` , `<'a>` represents that the functions gets the lifetime `'a` \(which is arbitary, there is no actual `'a` defined in the code, but it is the lifetime of the main function\).
* Argument definition `(x: &'a str, y: &'a str)` explicitly defines the lifetime of x and y that are passed as reference, 
* Return definition `-> &'a str` tells that the function will return a &reference to string \(because we are returning reference argument that we got\) that has a lifetime of `'a` will we got from the function.

  The result that is being returned \(reference to string in our case\) should have a lifetime of `'a`.

Now let's change our main body :

```rust
fn main() {
    let string1 = String::from("long string is long");
    {
        let string2 = String::from("xyz");
        let result = longest(string1.as_str(), string2.as_str());
        println!("The longest string is {}", result);
    }
}
```

Our code will compile successfully in this case because

* the returned result has a matches the lifetime of returned function

let's change our main body again :

```rust
fn main() {
    let string1 = String::from("long string is long");
    let result;
    {
        let string2 = String::from("xyz");
        result = longest(string1.as_str(), string2.as_str());
    }
    println!("The longest string is {}", result);
}
```

Now this will cause an error.

```text
error[E0597]: `string2` does not live long enough
 --> src/main.rs:6:44
  |
6 |         result = longest(string1.as_str(), string2.as_str());
  |                                            ^^^^^^^ borrowed value does not live long enough
7 |     }
  |     - `string2` dropped here while still borrowed
8 |     println!("The longest string is {}", result);
  |                                          ------ borrow later used here

error: aborting due to previous error

For more information about this error, try `rustc --explain E0597`.

To learn more, run the command again with --verbose.
```

The error shows that for result to be valid for the println! statement, string2 would need to be valid until the end of the outer scope. Rust knows this because we annotated the lifetimes of the function parameters and return values using the same lifetime parameter 'a.

#### Thinking in Terms of Lifetimes

The way in which you need to specify lifetime parameters depends on what your function is doing.

```rust
fn longest<'a>(x: &'a str, y: &str) -> &'a str {
    x
}
```

In this example, we’ve specified a lifetime parameter `'a` for the parameter x and the return type, but not for the parameter y, because the lifetime of y does not have any relationship with the lifetime of x or the return value.

... to be continued

## Structs in Rust

### Structures

#### Types of structures

* named-field structure : normal structure
* tuple struct : tuple like structure
* unit type struct : unit tuple like structures "\(\)"

### Named-field structures

#### Syntax

```rust
struct Person {
    pub name : String,
    pub age : u8
    size : (u8,u8)
    points : Vec<u8>
}
```

#### Declarations :

```rust
let uday = Person { 
    name : "Uday",
    age : 19,
    size : (78,186)    
}
```

**Accessing structure :** uday.name

**Note 1** : adding the keyword `pub` will make the struct public

**Note 2** : In-order to make the data members of a structure public, you have to add **pub** in front the field in order to make it public, because it is private by default, meaning only the file in which the structure is declared can access it.

### Tuple-like struct

#### Definition syntax

```rust
struct points(usize,usize);
```

#### Declaration syntax

```rust
let image_bounds = points(34,232);
```

**Accessing structure :** image\_bounds.1 \(Like accessing a tuple\)

**Note :** By default the members of tuple are private, and they need to made public explicitly

```rust
pub struct points(pub usize, pub usize)
```

### Unit-like structure

#### definition

```rust
struct OneSuch;
```

A value of such a type occupies no memory, much like the unit type \(\).

### Defining struct methods with impl

> ```rust
> struct Rectangle {
>     width: u32,
>     height: u32,
> }
>
> impl Rectangle {
>     fn area(&self) -> u32 {
>         self.width * self.height
>     }
> }
>
> fn main() {
>     let rect1 = Rectangle {
>         width: 30,
>         height: 50,
>     };
>
>     println!(
>         "The area of the rectangle is {} square pixels.",
>         rect1.area()
>     );
> }
> ```

#### Implementation

In order to create a member function, Rust syntax's doesn't allow declaring the function inside the struct. Rust do not have classes. So using `impl <T> {}`, we define function inside. The first parameter of every function that is being implemented for a struct has the argument **&self** which is similar to python.

**NOTE** : `&self` contains **&** as it is a reference to the struct. we cannot change the value of the data members of structure. For that we need `&mut self`.

### Associate Functions

Another useful feature of `impl` blocks is that we’re allowed to define functions within `impl` blocks that _don’t_ take `self` as a parameter. These are called _associated functions_ because they’re associated with the struct. They’re still functions, not methods, because they don’t have an instance of the struct to work with

**Example**

```rust
impl Rectangle {
    fn square(size: u32) -> Rectangle {
        Rectangle {
            width: size,
            height: size,
        }
    }
}
```

#### Multiple impl Blocks

Each struct is allowed to have multiple `impl` blocks. For example, Listing 5-15 is equivalent to the code shown in Listing 5-16, which has each method in its own `impl` block.

```rust
impl Rectangle {
    fn area(&self) -> u32 {
        self.width * self.height
    }
}

impl Rectangle {
    fn can_hold(&self, other: &Rectangle) -> bool {
        self.width > other.width && self.height > other.height
    }
}
```

### Generics Structs

Rust structs can be generic, meaning that their definition is a template into which you can plug whatever types you like

```rust
pub struct Queue<T> {
    older: Vec<T>,
    younger: Vec<T>
}
```

You can then make your implementations generic

```rust
impl<T> Queue<T> {
    pub fn new() -> Queue<T> {
        Queue { older: Vec::new(), younger: Vec::new() }
    } 
    pub fn push(&mut self, t: T) {
        self.younger.push(t);
    }
}
```

### Structs with lifetime parameter

#### Structs Containing References

Example :

```rust
struct S {
    r: &i32
} 
let s;
{
    let x = 10;
    s = S { r: &x };
}
assert_eq!(*s.r, 10);
```

**This program contains errors** : because the r in struct stores the reference of of x, as x goes out of scope, r has nothing to point to. So we get the error **expected lifetime parameter**.

