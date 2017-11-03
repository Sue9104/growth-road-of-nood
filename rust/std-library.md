# Std Library types

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