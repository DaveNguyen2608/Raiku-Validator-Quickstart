# Validator Quickstart



This guide explains how to get started with the **Raiku validator client**.

## System Requirements

### Minimum (testnet / learning)

- **CPU:** 16 cores
- **RAM:** 128 GB
- **Disk:** 1 TB NVMe
- **Network:** 1 Gbps

### Recommended

- **CPU:** 24–32 cores
- **RAM:** 256 GB
- **Disk:** 2 TB NVMe Gen4

---

## Get Started with the Raiku Validator Client

Our `raiku-agave` client is built on top of `jito-agave`.

If you're already running **Jito**, switching to **Raiku** only requires adding a few flags to your existing validator startup command.

**Jito Classic** and **Raiku** can coexist, which means no changes to your existing Jito configuration are required.

> **Note:** Raiku is **not compatible** with **Jito BAM**.

The Raiku validator is currently available as `raiku-agave` to pilot program partners and will be open-sourced at the end of the pilot program.

---

## Already Running `jito-agave`?

Follow the install process below, then add these flags to your existing validator startup command:

```bash
--raiku-engine-url https://engine.testnet.raiku.sh:443 \
--raiku-merkle-root-upload-authority 7maV3ghmAJZGmzCBa8xNWVkrz4S1WHiCXzAZhPufBY8e \
--raiku-commission-bps 500
```

That’s it. Your existing Jito flags stay unchanged.

---

## Building from Source

### 1. Install `rustc`, `cargo`, and `rustfmt`

```bash
curl https://sh.rustup.rs -sSf | sh
source $HOME/.cargo/env
rustup component add rustfmt
```

When building the `master` branch, make sure you are using the latest stable Rust version:

```bash
rustup update
```

When building a specific release branch, check the Rust version in `ci/rust-version.sh` and install it if needed:

```bash
rustup install VERSION
```

> **Note:** If this is not the latest Rust version installed on your machine, some `cargo` commands may require an override to use the correct version.

### 2. Install Build Dependencies

On Linux systems you may need packages such as `libssl-dev`, `pkg-config`, `zlib1g-dev`, and `protobuf`.

#### Ubuntu

```bash
sudo apt-get update
sudo apt-get install -y \
  libssl-dev \
  libudev-dev \
  pkg-config \
  zlib1g-dev \
  llvm \
  clang \
  cmake \
  make \
  libprotobuf-dev \
  protobuf-compiler
```

#### Fedora

```bash
sudo dnf install -y \
  openssl-devel \
  systemd-devel \
  pkg-config \
  zlib-devel \
  llvm \
  clang \
  cmake \
  make \
  protobuf-devel \
  protobuf-compiler \
  perl-core
```

### 3. Download the Source Code

```bash
export CARGO_NET_GIT_FETCH_WITH_CLI=true
git clone https://github.com/raiku-protocol/raiku-agave.git
cd raiku-agave
git submodule update --init --recursive
```

### 4. Build the Client

```bash
cargo build --release
```

---

## Next Step

After the build completes successfully, start your validator using your existing `jito-agave` setup and append the Raiku flags shown above.

---

## Notes

- Raiku is designed to work alongside **Jito Classic**
- No migration of your current Jito configuration is required
- **Do not use Raiku with Jito BAM**

---

## Support

If you are participating in the pilot program, follow the instructions provided by the Raiku team for validator onboarding, configuration, and environment-specific deployment details.
