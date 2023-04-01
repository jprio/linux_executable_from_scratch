To set the scene, let’s assume we want to make an exectuable binary for x86_64 Linux that’s supposed to be extremely portable. It should work on both Debian and Arch Linux. It should work on systems without glibc like Alpine Linux. It should even work in a FROM scratch Docker container. In a more serious setting you would statically link musl-libc with your Rust program, but today we’re in a silly-goofy mood so we’re going to try to make this work without a libc. And we’re also going to use Rust for this, more specifically the stable release channel of Rust, so this blog post won’t use any nightly-only features that might still change/break. If you’re using a Rust 1.0 version that was recent at the time of writing or later (>= 1.68.0 according to my computer), you should be able to try this at home just fine™.

Référence : https://vulns.xyz/2023/03/linux-executable-from-scratch-with-x86_64-unknown-none-rust/

Build : cargo build --release --target x86_64-unknown-none
Run : target/x86_64-unknown-none/release/linux_executable_from_scratch
Disassemble : objdump -d target/x86_64-unknown-none/release/linux_executable_from_scratch