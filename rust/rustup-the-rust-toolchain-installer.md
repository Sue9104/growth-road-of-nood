# Rustup (The Rust toolchain installer)

> Document: [Rustup readme](https://github.com/rust-lang-nursery/rustup.rs/blob/master/README.md)

## Configure environments
Save this file to **~/.zsh.after/rust.zsh**
```
export RUSTUP_DIST_SERVER=https://mirrors.ustc.edu.cn/rust-static​
export RUSTUP_UPDATE_ROOT=https://mirrors.ustc.edu.cn/rust-static/rustup​
```

## Configure rustup  
```
curl https://sh.rustup.rs -sSf | sh
```


* Enable tab completion for zsh

```
rustup completions zsh > ~/.zfunc/_rustup
echo fpath+=~/.zfunc >> ~/.zshrc
```

## Install specified version

```
rustup update
rustup install nightly
rustup default nightly
rustup self update
```
> **nightly** is for active development, **beta** is for testing and bugfixing, and **stable** is for final releases.

## override precedence

```
rustup override set 1.0.0
rustup override unset .
```
Prefered in this order:
* An explicit toolchain, e.g. cargo +beta
* The RUSTUP_TOOLCHAIN environment variable
* A directory override, ala rustup override set beta
* The rust-toolchain file
* The default toolchain

## Cross-compilation

```
rustup target list
rustup target add x86_64-unknown-linux-musl
cargo build --target x86_64-unknown-linux-musl --release
```
* web应用：wasm32-unknown-emscripten
* Android应用：arm-linux-androideabi