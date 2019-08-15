# cargo

## 创建

```rust
cargo new my_crate
cargo new my_crate --bin
```

## 工作空间

工作空间 是一系列共享同样的 Cargo.lock 和输出目录的包。

### 指定工作空间的依赖

in **cargo.toml**

```
[dependencies]
add-one = { path = "add-one" }
```

### 依赖外部 crate

只有一个顶级的 **cargo.lock**，这确保了所有的 crate 都使用完全相同版本的依赖。

### 测试

```
cargo test -all
```

## build
1. 指定平台 ```--target```
```rust
cargo build --target x86_64-unknown-linux-musl --release
```
2. 指定rust版本 ```+nightly```
```rust
cargo +nightly build
rustup run nightly cargo build
```

## 注释

```rust
cargo doc --open
```

符号：

* /// markdown 注释
* //! 项注释
* //\`\`\` 示例代码，会测试

场景：

* Panics：这个函数可能会 panic! 的场景。并不希望程序崩溃的函数调用者应该确保他们不会在这些情况下调用此函数。
* Errors：如果这个函数返回 Result，此部分描述可能会出现何种错误以及什么情况会造成这些错误，这有助于调用者编写代码来采用不同的方式处理不同的错误。
* Safety：如果这个函数使用 unsafe 代码（这会在第十九章讨论），这一部分应该会涉及到期望函数调用者支持的确保 unsafe 块中代码正常工作的不变条件（invariants）。

## 共有API

```rust
pub use
```

## 发布

```rust
cargo publish
cargo yank --vers 1.0.1
cargo yank --vers 1.0.1 --undo
```



