# Yarrr

> Board every file with **YARA precision** – and do it fast, safe, and sailor‑simple.

[![Build](https://github.com/yourorg/yarrr/actions/workflows/build.yaml/badge.svg)](https://github.com/yourorg/yarrr/actions)
[![Crates.io](https://img.shields.io/crates/v/yarrr-cli.svg)](https://crates.io/crates/yarrr-cli)
[![License: MIT OR Apache‑2.0](https://img.shields.io/badge/license-MIT%20OR%20Apache--2.0-blue.svg)](LICENSE)

Yarrr is a blazing‑fast, cross‑platform file scanner written in Rust. It harnesses the full power of YARA (or the pure‑Rust **yara‑x** engine) to uncover malware, secrets, and anything else you can describe with rules—while keeping the user experience joyful.

---

## ⚓ Features at a Glance

| Status         | Feature                  | Notes                                    |
| -------------- | ------------------------ | ---------------------------------------- |
| ✅ Must‑have    | Recursive directory scan | `yarrr scan <path>`                      |
| ✅ Must‑have    | Load multiple rule sets  | Accepts local paths & glob patterns      |
| ✅ Must‑have    | Exit codes for CI        | 0 (clean) / 10 (matches) / >1 (error)    |
| 🚀 One‑dim     | Hyper‑parallel core      | `rayon`‑driven, scales with CPUs         |
| 🚀 One‑dim     | Memory‑mapped reads      | Fast large‑file scanning                 |
| ✨ Attractive   | Live file watch          | `yarrr watch <path>`                     |
| ✨ Attractive   | JSON / Protobuf output   | Pipe to SIEM, Splunk, Grafana            |
| ✨ Attractive   | Progress bars            | Smooth ETA & per‑file status             |
| 🪄 Magic       | `yarrr rule pull`        | One‑command sync of community rule packs |
| 🪄 Magic       | Rule lockfile & updates  | Deterministic builds like Cargo.lock     |
| 🪄 Magic       | Smart quarantine         | Optional auto‑move of detected files     |
| 🤝 Indifferent | GUI wrapper              | Not planned for CLI‑centric users        |

---

## 📦 Installation

```bash
cargo install yarrr-cli --features "yara-x"
# or grab binaries from Releases if you prefer libyara
```

> **Prerequisites:** Rust 1.76+ and (if using libyara) the `yara` C library & headers.

---

## 🏃 Quick start

```bash
# Scan the current directory with bundled rules
yarrr scan .

# Scan Downloads with custom rule sets & JSON output
yarrr scan ~/Downloads --ruleset rules/malware.yar --json
```

---

## 📚 Rule management

```bash
# Pull the latest community pack
yarrr rule pull community

# Freeze current rule versions
yarrr rule pin community@2025‑06‑01
```

Collected rule packs live in `~/.yarrr/rules/` by default.

---

## 🛡️ Security

* Written in safe Rust wherever possible
* Optional pure‑Rust backend for zero‑FFI builds
* Supports sandboxing via seccomp/cap\_drop on Linux
* Bench‑tested with `cargo‑fuzz` corpus & CI runtime checks

---

## 🗺️ Roadmap

1. Plugin SDK for custom file decoders
2. WASI build for scanning in WebAssembly sandboxes
3. AI‑assisted rule authoring (research phase)

---

## 🤝 Contributing

Pull requests are welcome! See [`CONTRIBUTING.md`](CONTRIBUTING.md) and open a discussion if you’d like to tackle a feature.
