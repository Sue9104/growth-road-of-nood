# Std Library types

## struct

```rust
struct Rectangle {
    length: i32,
    heigth: i32,
}
```

## Turple

```rust
let pair = (1,2);
```

## Box
A box is a smart pointer to a heap allocated value of type T. Boxed values can be dereferenced using the * operator.

```rust
use std::mem;
struct Point {
    x: f64,
    y: f64,
}

fn main() {
    let a = Point{x: 0.1, y: 0.2};
    println!("Point Size: {}",   mem::size_of_val(&a));
    let b: Box<Point> = Box::new(a);
    println!("Point Size: {}", mem::size_of_val(&b));
    
    let c = *b;
    println!("Point Size: {}", mem::size_of_val(&c));
}
```

## Vectors
Vectors are re-sizable arrays. A vector is represented using 3 words: a pointer to the data, its length, and its capacity. Iterators can be collected into vectors

```rust
fn main() {
    let mut xs = vec![1i32, 2, 3];
    xs.push(4);
    println!("Vector size: {}", xs.len());
    for x in xs.iter(){
        println!("{"?}", x);
    }
}
```

## Strings
std::str & std::string

- A String is stored as a vector of bytes (Vec<u8>),  heap allocated, growable and not null terminated.

- str is a slice (&[u8]) that always points to a valid UTF-8 sequence, and can be used to view into a String, just like &[T] is a view into Vec<T>.

```rust
fn main() {
    let pangram: &'static str = "the quick brown fox jumps over the lazy dog";
    let mut chars: Vec<char> = pangram.chars().collect();
    chars.sort();
    chars.dedup();
}
```

## Option
The Option<T> enum has two variants:
- None, to indicate failure or lack of value, and
- Some(value), a tuple struct that wraps a value with type T.

## Result
The Result<T, E> enum has two variants:
- Ok(value) which indicates that the operation succeeded, and wraps the value returned by the operation. (value has type T)
- Err(why), which indicates that the operation failed, and wraps why, which (hopefully) explains the cause of the failure. (why has type E)

> ? is used at the end of an expression returning a Result

## Caveat

| type  | unit  | 
|:--:|:--:|
| vector  | vec[0]  |
| turple  | turple.0  | 
| hashmap  | hashmap.get("a")  |
|struct| struct.a |
|enum| enum::a | 