# ⚡ Super Compressor

A high-performance, production-grade compression utility and multi-format extraction engine written entirely in **Rust**. Engineered for maximum data density, it leverages solid archiving pipelines, max-level codecs, and intelligent entropy-aware storage bypass rules to minimize archive footprints without losing a single bit. 

Wrapped in a beautiful, custom frameless, hardware-accelerated **egui** UI featuring a dark neon cyberpunk terminal palette.

---

## 🚀 Key Architectural Features

* **Intelligent Lossless Tuning (`Ultra`)**: Combines solid-tar bundling with max-level backend codecs (`Zstd 22`, `Brotli 11`, `LZMA2 Max`).
* **Entropy-Aware Storage Bypass**: Detects pre-compressed file signatures (`mp4`, `jpg`, `7z`, etc.) dynamically and applies a straight `STORE` operation to eliminate CPU cycles and archival bloat.
* **AppImage Deep Inspection & Unpacking**: Decodes both legacy `Type1 (ISO9660)` and modern `Type2 (SquashFS)` layouts. It systematically drops down an execution cascade from the official `--appimage-extract` binary extraction loop, to offset-calculated `unsquashfs` execution, down to standard static stream utilities.
* **Robust Decoding Fallbacks**: Built-in deterministic routing for single-file codecs (`zst`, `gz`, `xz`, `bz2`, `br`) and comprehensive container unpacking (`zip`, `7z`, `tar.*`, `rar`).
* **Frameless Hardware-Accelerated Frontend**: High-fidelity rendering with custom OS window decoration bindings, real-time logging, and interactive asynchronous progress monitoring.
* **Integrated Deterministic Selftest Suite**: Built-in verification routine (`--selftest`) executing full-cycle roundtrip operations over multiple formats to guarantee compression safety and baseline data integrity.

---

## 🛠 Tech Stack

* **Core Engine**: Rust (Safe, zero-overhead systems programming layer).
* **Compression Backends**: `zstd`, `xz2`, `flate2`, `bzip2`, `brotli`, `sevenz-rust`, `tar`, `zip`.
* **Graphical Framework**: `egui` & `eframe` (Immediate-mode rendering).
* **Native Overrides**: `rfd` (Native system file dialogue routing).

---

## ⚙️ Installation & Usage

### Prerequisites
Ensure you have the Rust toolchain installed. For fallback extraction engines, it is recommended to have standard platform utilities available in your `PATH`:
```bash
# Ubuntu/Debian fallback utilities
sudo apt install squashfs-tools libarchive-tools p7zip-full unrar
```

### Build from Source
```bash
# Clone the repository
git clone https://github.com
cd super-compressor

# Build performance-optimized release binary
cargo build --release
```

### Execution Flags
```bash
# Launch the Graphical User Interface
./target/release/super_compressor

# Execute engine self-test routines to verify lossless integrity
./target/release/super_compressor --selftest
```

---

## 🧬 Engine Multi-Format Pipeline Matrix

| Format Target | Backend Codec Strategy | Primary Practical Ideal Use Case |
| :--- | :--- | :--- |
| `tar.zst` | Solid Tarball + Zstd L22 + Long-Distance Matching | **Best Overall** (Massive data footprints / repositories) |
| `7z` | Staged LZMA2 Ultra Solid Container | **Best Mixed Documentation Density** |
| `zip` | Deflate L9 with Predictive Metadata Stream Routing | **Maximum Platform Interoperability** |
| `tar.br` | Solid Tarball + Brotli L11 Context Modeling | High-Density Text / Source-Code Archiving |
| `Single File` | Isolated Stream Encapsulation (`zst`, `gz`, `xz`, etc.) | Direct Stream Processing / Log Rotation |

---

## 🛡 Lossless Guarantee & Safety
The engine guarantees complete bitwise reproducibility. If an input format has low entropy (pre-compressed data), the utility bypasses outer compression envelopes gracefully to maintain format validity without artifact generation.
