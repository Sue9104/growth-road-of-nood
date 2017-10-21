# Rustup (The Rust toolchain installer)

> Document: [Rustup readme](https://github.com/rust-lang-nursery/rustup.rs/blob/master/README.md)

## Configure environments
Save this file to **~/.zsh.after/**
```
export RUSTUP_HOME=$HOME/.rustup​
export RUSTUP_DIST_SERVER=https://mirrors.ustc.edu.cn/rust-static​
export RUSTUP_UPDATE_ROOT=https://mirrors.ustc.edu.cn/rust-static/rustup​
[ -e "$HOME/.cargo/env" ] && source $HOME/.cargo/env
```

## Configure rustup  
```
curl https://sh.rustup.rs -sSf | 
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

. Add MUSL target rustup target add x86_64-unknown-linux-musl
4. Build your binary with cargo cargo build --target x86_64-unknown-linux-musl --release


2. release versionnightly is for active development,beta is for testing and bugfixingand stable is for final releases.
3. override precedence rustup override set 1.0.0rustup override unset .An explicit toolchain, e.g. cargo +betaThe RUSTUP_TOOLCHAIN environment variableA directory override, ala rustup override set betaThe rust-toolchain fileThe default toolchain
4. Cross-compilation rustup target listrustup target add x86_64-unknown-linux-muslcargo build --target x86_64-unknown-linux-musl  --releasewasm32-unknown-emscripten web应用arm-linux-androideabi Androideabi 应用