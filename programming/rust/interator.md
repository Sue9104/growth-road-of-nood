# iterator

## diff iterator

* iter\(\) ：迭代器的不可变引用
* into\_iter\(\) ：拥有所有权的迭代器
* iter\(\) ：迭代器的可变引用

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

* map
* filter 一般跟闭包
* chain 两个迭代器合并为一个array
* zip 两个迭代器合并为一个tuple
* enumerate 序号＋值

## consuming adaptors

调用next的方法

* sum

## build own iterator

通过定义next方法来实现Iterator trait 来创建自定义迭代器

```rust
// 初始化结构体
struct Counter {
    count: u32,
}

impl Counter {
    fn new() -> Counter {
        Counter { count: 0 }
    }
}

//创建next方法
impl Iterator for Counter {
    type Item = u32;

    fn next(&mut self) -> Option<Self::Item> {
        self.count += 1;

        if self.count < 6 {
            Some(self.count)
        } else {
            None
        }
    }
}

//消费迭代器
#[test]
fn using_other_iterator_trait_methods() {
    let sum: u32 = Counter::new().zip(Counter::new().skip(1))
                                 .map(|(a, b)| a * b)
                                 .filter(|x| x % 3 == 0)
                                 .sum();
    assert_eq!(18, sum);
}
```

