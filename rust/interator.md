# Iterator

## collect 
将迭代器生成的一系列的值转换为vector
```rust
use std::env;
fn main() {
    let args: Vec<String> = env::args().collect();
    println!("{:?}", args);
}
```