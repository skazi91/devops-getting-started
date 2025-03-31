# 🧰 Linux CLI Toolkit – Hidden Gems for Power Users

These tools will level up your command-line game. Most are available via `apt`, `brew`, or your favorite package manager.

---

## 📋 Text & Log Utilities
| Tool | Use |
|------|-----|
| `bat` | A better `cat` with syntax highlighting |
| `less` | Scroll through long text with `/search` support |
| `jq` | Format and parse JSON from APIs or logs |
| `awk`, `sed` | Power-text processing (great for logs, configs) |

---

## 🖥️ System Info & Diagnostics
| Tool | Use |
|------|-----|
| `htop` | Interactive resource monitor (CPU/RAM) |
| `glances` | Real-time multi-stat monitor (cross-platform) |
| `dstat` | Combines iostat, netstat, vmstat |
| `ncdu` | Visual disk usage analyzer |
| `neofetch` | System summary banner |

---

## 🌐 Networking Tools
| Tool | Use |
|------|-----|
| `nmap` | Scan ports & networks |
| `ss` / `netstat` | View open sockets & connections |
| `iperf3` | Test bandwidth and latency |
| `traceroute`, `mtr` | Track packet routes |
| `dig`, `whois` | DNS and domain tools |

---

## 📦 File & Process Helpers
| Tool | Use |
|------|-----|
| `fd` | Better alternative to `find` |
| `ripgrep (rg)` | Lightning-fast `grep` |
| `xargs` | Run commands on lists of items |
| `killall`, `pkill` | Kill processes by name or user |

---

## 🔧 DevOps Bonus Tools
| Tool | Use |
|------|-----|
| `curl`, `httpie` | HTTP clients (test APIs) |
| `watch` | Repeat commands every few seconds |
| `tmux` | Terminal multiplexer (tabs/split panes) |
| `fzf` | Fuzzy file finder |
| `tldr` | Simple command usage examples |

---

## 🔍 Try This:
```bash
sudo apt install bat ripgrep fzf glances ncdu mtr httpie tldr -y
```
Then run:
```bash
tldr tar
bat ~/.bashrc
ncdu /
fzf
```

---

## 🧠 Learn More
- [https://tldr.sh/](https://tldr.sh/)
- [https://github.com/sharkdp/bat](https://github.com/sharkdp/bat)
- `man`, `--help`, and `cheat.sh` are your friends!
