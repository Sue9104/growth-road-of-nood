# Iterator
## diff iterator
- iter() ：迭代器的不可变引用
- into_iter() ：拥有所有权的迭代器
- iter() ：迭代器的可变引用

## collect 
将迭代器生成的一系列的值转换为vector
```rust
use std::env;
fn main() {
    let args: Vec<String> = env::args().collect();
    println!("{:?}", args);
}
```

## iterator adaptors
产生其他的迭代器
- map
- filter

## consuming adaptors
调用next的方法
- sum

