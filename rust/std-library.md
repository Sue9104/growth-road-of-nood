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