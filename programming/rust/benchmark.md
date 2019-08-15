# Benchmark tests

https://doc.rust-lang.org/1.1.0/test/

## Bencher

Required Method: iter 

```rust
    #[bench]
    fn bench_add_two(b: &mut Bencher) {
        b.iter(|| add_two(2));
    }
```

## black_box

Compiler might recognize that some calculation has no external effects and remove it entirely.
- ```iter``` receives can return an arbitrary value which forces the optimizer to consider the result used.

```rust
b.iter(|| {
    // note lack of `;` (could also use an explicit `return`).
    (0..1000).fold(0, |old, new| old ^ new)
});
```

- black_box: forces optimizer to consider any argument as used.

```rust
b.iter(|| {
    let n = test::black_box(1000);

    (0..n).fold(0, |a, b| a ^ b)
});
```