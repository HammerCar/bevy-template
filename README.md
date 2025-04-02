# Bevy Template

This repository has a template Bevy project with all the performance optimizations listed on Bevy's [Quick Start Guide](https://bevyengine.org/learn/quick-start/introduction/).

## Version

The current Bevy version this template is built for is `0.15.3`

## Prerequisites

### Rust and Bevy dependencies

You need to have rust nightly and OS dependencies required by Bevy installed. Refer to the [Rust Setup](https://bevyengine.org/learn/quick-start/getting-started/setup/#rust-setup) section on the Bevy Quick Start Guide if you haven't already set those up.

### Linker

Use a faster linker. Differs based on development platform.

- **Linux:** Use Mold
  - **Ubuntu:** `sudo apt-get install mold clang`
  - **Fedora:** `sudo dnf install mold clang`
  - **Arch:** `sudo pacman -S mold clang`
- **Windows:** Use LLD. Ensure you have the latest [cargo-binutils](https://github.com/rust-embedded/cargo-binutils) as this lets commands like cargo run use the LLD linker automatically.

  ```sh
  cargo install -f cargo-binutils
  rustup component add llvm-tools-preview
  ```

- **MacOS:** On MacOS, the default system linker ld-prime is fastest.

### Codegen

Using Cranelift is about 30% faster at compiling than LLVM.

Install Cranelift

```sh
rustup component add rustc-codegen-cranelift-preview --toolchain nightly
```
