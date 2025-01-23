# Minimal Rust OS

A bare metal operating system implementation written in Rust, running without the standard library (`no_std`). This project demonstrates fundamental OS concepts using Rust's zero-cost abstractions and memory safety features.

## Project Overview

This implementation follows a step-by-step approach:

1. **Bare Metal Binary**: Created a freestanding Rust binary without standard library dependencies
2. **Basic Kernel**: Implemented a minimal kernel that boots and displays "Hello World" through QEMU
3. **VGA Text Mode**: Added support for screen output using VGA text mode buffer
4. **Testing Framework**: Implemented comprehensive unit and integration tests

## Requirements

- Rust nightly (at least 2020-07-15)
- QEMU for system emulation
- `bootimage` tool for creating bootable disk images

## Building

First, ensure you have the latest nightly toolchain:
```
rustup update nightly --force
```

Install the bootimage tool:
```
cargo install bootimage
```

Build the project:
```
cargo build
cargo bootimage
```

This creates a bootable disk image in `target/x86_64-blog_os/debug`.

## Running

Launch the OS in QEMU:
```
cargo run
```

For booting on real hardware (Linux):
```
dd if=target/x86_64-blog_os/debug/bootimage-blog_os.bin of=/dev/sdX && sync
```
**Warning**: Replace `sdX` with your USB device. Be extremely careful with the device name!

## Testing

Run the test suite:
```
cargo xtest
```

---

This project is based on [phil-opp/blog_os](https://github.com/phil-opp/blog_os/blob/post-04/README.md) and follows the ["Writing an OS in Rust"](https://os.phil-opp.com) blog series.