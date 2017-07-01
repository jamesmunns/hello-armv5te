# Minimal example for Rust on ARMv5te

This template uses the atomic operations provided by linux (via libgcc) to enable use of Arc, and all parts that depend 
on it from `std`.

## Current unknowns/issues

* Uses `alloc_system` rather than `jemalloc`
* Uses `abort=panic` rather than `unwind`
* Dependency crates should work, however I already ran into some issues with `openssl-sys`...

## Dependencies

* Rust nightly
    * `rustup install nightly && rustup default nightly`
* Rust src
    * `rustup component add rust-src`
* Xargo
    * `cargo install xargo`
* A cross compiled GCC for `armv5te`, e.g. `arm-buildroot-linux-gnueabi-gcc`
    * The cross compiler must be in your PATH.
    * `export PATH=/path/to/your/gcc:$PATH`

## Usage

```bash
cd hello-armv5te
source ./env_file

xargo build
file target/armv5te-unknown-linux-gnueabi-osatomic/debug/armv5te_demo

xargo build --release
file target/armv5te-unknown-linux-gnueabi-osatomic/release/armv5te_demo
```
