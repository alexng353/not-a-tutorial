[Benchmarking programs in Rust ](https://stackoverflow.com/a/40953863)

```rust
fn main() {
    use std::time::Instant;
    let now = Instant::now();

    // Code block to measure.
    {
        my_function_to_measure();
    }

    let elapsed = now.elapsed();
    println!("Elapsed: {:.2?}", elapsed);
}
```