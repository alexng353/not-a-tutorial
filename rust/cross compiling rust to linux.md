https://github.com/rust-lang/rust/issues/34282

```bash
rustup target add x86_64-unknown-linux-gnu
brew tap SergioBenitez/osxct
brew install x86_64-unknown-linux-gnu
CARGO_TARGET_X86_64_UNKNOWN_LINUX_GNU_LINKER=x86_64-unknown-linux-gnu-gcc cargo build --release --target=x86_64-unknown-linux-gnu
```

[https://doc.rust-lang.org/cargo/reference/config.html](https://doc.rust-lang.org/cargo/reference/config.html "https://doc.rust-lang.org/cargo/reference/config.html") [https://www.reddit.com/r/rust/comments/g1w6ki/cross_compilation_mac_osx/](https://www.reddit.com/r/rust/comments/g1w6ki/cross_compilation_mac_osx/ "https://www.reddit.com/r/rust/comments/g1w6ki/cross_compilation_mac_osx/") [https://github.com/rust-lang/cargo/issues/4399](https://github.com/rust-lang/cargo/issues/4399 "https://github.com/rust-lang/cargo/issues/4399")

```
-   `$CARGO_HOME/config.toml` which defaults to:
    -   Windows: `%USERPROFILE%\.cargo\config.toml`
    -   Unix: `$HOME/.cargo/config.toml`
```

```toml
[target.aarch64-unknown-linux-gnu]
linker = "aarch64-unknown-linux-gnu-gcc" # https://github.com/thinkski/osx-arm-linux-toolchains


[target.x86_64-unknown-linux-gnu]
linker = "x86_64-unknown-linux-gnu-gcc" # https://github.com/messense/homebrew-macos-cross-toolchains
```
