# Installing rbspy

Installing rbspy is easy on most platforms, as it's a single binary. It can run on your computer, in CI, or on production servers.

## System requirements

### Operating system

rbspy runs on Linux\*, Windows, FreeBSD, and macOS.

\* Linux kernel version 3.2+ required. For Ubuntu, this means Ubuntu 12.04 or newer.

### Ruby

rbspy can profile programs that use Ruby 1.9.3 and newer. The maintainers try to add support for new Ruby versions shortly after they're released.

## Option 1: Install from a package

Installing from a package is the simplest method. If your preferred operating system or distribution isn't listed here, please consider making a package for it. We are grateful for packaging contributions.

### Alpine Linux

```
apk add rbspy
```

### macOS (Homebrew)

```
brew install rbspy
```

## Option 2: Download a binary

If there's no package for your operating system, downloading a pre-compiled binary is the next simplest method. There are binaries for Linux, macOS, FreeBSD, and Windows, which are the supported platforms.

1. Download the latest release for your operating system from [the releases page](https://github.com/rbspy/rbspy/releases)
    - Note: There are two types of Linux releases. Those tagged with `gnu` are dynamically linked against GNU libc, which needs to be installed on the system where rbspy runs. Those tagged with `musl` are statically linked against musl libc and can be used without a specific libc being installed.
2. Unpack the release. On Unix systems (Linux, Mac, FreeBSD), move the rbspy binary to `/usr/local/bin/rbspy`. You will need to make it executable with, for example, `chmod +x rbspy`.
3. Run the binary to start profiling! See [Using rbspy](./using-rbspy.md) to get started.

### Containers (Docker, podman, etc)

If you're installing rbspy in a containerized environment, please have a look at the images we publish on [Docker Hub](https://hub.docker.com/r/rbspy/rbspy/tags). Each image has support for x86_64 (Intel) and aarch64 (ARM) CPUs, and there are separate tags for glibc and musl as noted above.

## Option 3: Build rbspy from source

Finally, you can build rbspy from source if you have a Rust toolchain installed. You will need **Rust 1.56 or newer**.

1. Install Cargo (if you haven't already). There may be a package available for your operating system. There's a guide in the [cargo docs](https://doc.rust-lang.org/cargo/getting-started/installation.html), or you can run this command if you're on Linux, macOS, or FreeBSD:

    ```
    curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
    ```

    For other systems, please check the instructions at https://rustup.rs/.

2. Add `~/.cargo/bin` to your `PATH`:

    ```
    . "$HOME/.cargo/env"
    ```

3. Build rbspy!

    ```
    git clone https://github.com/rbspy/rbspy
    cd rbspy
    cargo build --release
    ./target/release/rbspy --help
    ```

    Alternatively, you can build and install from crates.io:

    ```
    cargo install rbspy --locked
    ```
    