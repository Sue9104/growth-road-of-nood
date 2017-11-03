# trait
trait 类似于其他语言中的常被称为 接口（interfaces）的功能，是一种将方法签名组合起来的方法。```impl trait for structor```

```rust
pub trait Summarizable {
    fn summary(&self) -> String;
}
pub struct NewsArticle {
    pub headline: String,
    pub location: String,
    pub author: String,
    pub content: String,
}

impl Summarizable for NewsArticle {
    fn summary(&self) -> String {
        format!("{}, by {} ({})", self.headline, self.author, self.location)
    }
}
```

## trait bounds
将泛型被限制为那些实现了特定 trait 的类型

```rust
pub fn notify<T: Summarizable>(item: T) {
    println!("Breaking news! {}", item.summary());
}

fn some_function<T, U>(t: T, u: U) -> i32
    where T: Display + Clone,
          U: Clone + Debug 
 {
     ...
 }
```

## method
方法被调用的结构体的实例,第一个参数总是self,```impl structor```, 调用structor.method()

```rust
struct Rectangle {
    length: u32,
    width: u32,
}

impl Rectangle {
    fn area(&self) -> u32 {
        self.length * self.width
    }

```

### associated functions

impl块中定义不 以 self 作为参数的函数，调用structor::function()

```rust
impl Rectangle {
    fn square(size: u32) -> Rectangle {
        Rectangle { length: size, width: size }
    }
}
```
