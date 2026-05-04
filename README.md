```ruby
        ██╗  ██╗ █████╗ ███████╗██╗  ██╗       █████╗ ██╗   ██╗██████╗ ██╗████████╗
        ██║  ██║██╔══██╗██╔════╝██║  ██║      ██╔══██╗██║   ██║██╔══██╗██║╚══██╔══╝
        ███████║███████║███████╗███████║█████╗███████║██║   ██║██║  ██║██║   ██║   
        ██╔══██║██╔══██║╚════██║██╔══██║╚════╝██╔══██║██║   ██║██║  ██║██║   ██║   
        ██║  ██║██║  ██║███████║██║  ██║      ██║  ██║╚██████╔╝██████╔╝██║   ██║   
        ╚═╝  ╚═╝╚═╝  ╚═╝╚══════╝╚═╝  ╚═╝      ╚═╝  ╚═╝ ╚═════╝ ╚═════╝ ╚═╝   ╚═╝   
```


> Multi-threaded hash cracking tool with dictionary, brute-force, and rule-based mutation attacks.
> 
<img width="1536" height="1024" alt="ChatGPT Image Apr 22, 2026, 05_42_45 PM" src="https://github.com/user-attachments/assets/9ade1a72-6ccd-4f34-961a-e68e68b052f9" />

## What It Does

- Crack MD5, SHA1, SHA256, and SHA512 hashes with auto-detection from hash length
- Dictionary attacks using memory-mapped wordlists for zero-copy large file handling
- Brute-force attacks with configurable character sets and keyspace partitioning
- Rule-based mutations (capitalize, leet speak, digit append, reverse, toggle case)
- Multi-threaded with zero-contention work partitioning across all CPU cores
- Salt support with prepend/append positioning
- Rich terminal progress display with speed, ETA, and progress bar

## Quick Start

```bash
./install.sh
hashcracker --hash 5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8 \
  --wordlist wordlists/10k-most-common.txt
# ✔ CRACKED: password
```

> [!TIP]
> This project uses [`just`](https://github.com/casey/just) as a command runner. Type `just` to see all available commands.
>
> Install: `curl -sSf https://just.systems/install.sh | bash -s -- --to ~/.local/bin`

## Demo Hashes

Try these — all crack instantly against the included wordlist:

| Hash | Type | Plaintext |
|------|------|-----------|
| `5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8` | SHA256 | password |
| `8621ffdbc5698829397d97767ac13db3` | MD5 | dragon |
| `ed9d3d832af899035363a69fd53cd3be8f71501c` | SHA1 | shadow |

```bash
hashcracker --hash 8621ffdbc5698829397d97767ac13db3 --wordlist wordlists/10k-most-common.txt
hashcracker --hash ed9d3d832af899035363a69fd53cd3be8f71501c --wordlist wordlists/10k-most-common.txt --rules
hashcracker --hash 5e884898da28047151d0e56f8dc6292773603d0d6aabbdd62a11ef721d1542d8 --bruteforce --charset lower --max-length 8
```
