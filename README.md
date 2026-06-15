```ruby
                ██╗  ██╗ █████╗ ███████╗██╗  ██╗       █████╗ ██╗   ██╗██████╗ ██╗████████╗
                ██║  ██║██╔══██╗██╔════╝██║  ██║      ██╔══██╗██║   ██║██╔══██╗██║╚══██╔══╝
                ███████║███████║███████╗███████║█████╗███████║██║   ██║██║  ██║██║   ██║   
                ██╔══██║██╔══██║╚════██║██╔══██║╚════╝██╔══██║██║   ██║██║  ██║██║   ██║   
                ██║  ██║██║  ██║███████║██║  ██║      ██║  ██║╚██████╔╝██████╔╝██║   ██║   
                ╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝      ╚═╝  ╚═╝ ╚═════╝ ╚═════╝ ╚═╝   ╚═╝   
```
## Overview

Hash-Audit is a command-line security research utility designed for auditing password hashes. It supports automatic hash-type detection, memory-efficient wordlist processing, and parallelised cracking across all available CPU cores.

---
<img width="1536" height="1024" alt="ChatGPT Image Apr 22, 2026, 05_42_45 PM" src="https://github.com/user-attachments/assets/9ade1a72-6ccd-4f34-961a-e68e68b052f9" />

---

## Features

| Capability | Details |
|---|---|
| **Hash Algorithms** | MD5, SHA1, SHA256, SHA512 — auto-detected from hash length |
| **Attack Modes** | Dictionary, Brute-Force, Rule-Based Mutation |
| **Wordlist Handling** | Memory-mapped I/O for zero-copy processing of large files |
| **Brute-Force** | Configurable character sets with keyspace partitioning |
| **Rule Mutations** | Capitalise, leet-speak, digit append, reverse, toggle case |
| **Parallelism** | Zero-contention work partitioning across all CPU cores |
| **Salt Support** | Prepend or append positioning |
| **Progress Display** | Live terminal UI — speed, ETA, and progress bar |

---

## Installation

```bash
./install.sh
```

> **Note:** This project uses [`just`](https://github.com/casey/just) as a command runner.
> Run `just` to list all available commands.
>
> **Install `just`:**
> ```bash
> curl -sSf https://just.systems/install.sh | bash -s -- --to ~/.local/bin
> ```

---

## Quick Start

```bash
hashcracker \
  --hash 5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8 \
  --wordlist wordlists/10k-most-common.txt

# Output: ✔ CRACKED: password
```

---

## Demo Hashes

The following hashes are included for testing and crack instantly against the bundled wordlist:

| Hash | Algorithm | Plaintext |
|---|---|---|
| `5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8` | SHA256 | `password` |
| `8621ffdbc5698829397d97767ac13db3` | MD5 | `dragon` |
| `ed9d3d832af899035363a69fd53cd3be8f71501c` | SHA1 | `shadow` |

### Example Commands

**Dictionary attack (MD5):**
```bash
hashcracker \
  --hash 8621ffdbc5698829397d97767ac13db3 \
  --wordlist wordlists/10k-most-common.txt
```

**Dictionary attack with rule mutations (SHA1):**
```bash
hashcracker \
  --hash ed9d3d832af899035363a69fd53cd3be8f71501c \
  --wordlist wordlists/10k-most-common.txt \
  --rules
```

**Brute-force attack (SHA256, lowercase, max 8 characters):**
```bash
hashcracker \
  --hash 5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8 \
  --bruteforce \
  --charset lower \
  --max-length 8
```

---

## Documentation

In-depth coverage of security theory, architecture, and step-by-step walkthroughs is available in the [Learn Modules](#learn).

---

## License

See [`LICENSE`](./LICENSE) for terms of use.
