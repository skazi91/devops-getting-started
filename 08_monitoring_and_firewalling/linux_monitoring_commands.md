# 📊 Linux Monitoring Commands Cheat Sheet

A collection of essential Linux monitoring commands to observe system performance, diagnose issues, and track network or resource usage.

---

## 🧠 System Load & Processes
| Command | Description |
|---------|-------------|
| `top` | Real-time process monitor (CPU, memory, PID info) |
| `htop` | Enhanced version of `top` with color and interactivity |
| `uptime` | Shows how long system has been running and load averages |
| `vmstat 1` | Displays system memory, processes, and I/O every second |
| `ps aux` | Detailed list of all processes |

---

## 💽 Disk Usage
| Command | Description |
|---------|-------------|
| `df -h` | Show disk space usage (human-readable) |
| `du -sh *` | Show sizes of folders/files in current directory |
| `lsblk` | List all block devices (partitions, disks) |

---

## 🧵 Memory & Swap
| Command | Description |
|---------|-------------|
| `free -m` | Show memory and swap usage in MB |
| `cat /proc/meminfo` | Detailed memory stats from the kernel |

---

## 🌐 Network Monitoring
| Command | Description |
|---------|-------------|
| `ip a` or `ifconfig` | Show network interfaces and IPs |
| `ss -tuln` | List listening ports with protocols |
| `netstat -tulnp` | Show active connections and their programs |
| `ping 8.8.8.8` | Test basic internet connectivity |
| `traceroute google.com` | Show route packets take |
| `nmap -sP 192.168.1.0/24` | Ping scan your local network |
| `tcpdump -i eth0` | Capture live packet traffic (use with care) |

---

## 📦 Disk I/O
| Command | Description |
|---------|-------------|
| `iotop` | Show real-time disk I/O per process (requires root) |
| `iostat` | CPU and I/O statistics (from `sysstat` package) |
| `dstat` | Combines vmstat, iostat, netstat in one tool |

---

## 🔍 System Logs
| Command | Description |
|---------|-------------|
| `journalctl -xe` | Show recent logs with errors |
| `dmesg` | Kernel ring buffer (boot + hardware info) |
| `tail -f /var/log/syslog` | Follow system logs in real time |

---

## 💡 Tips
- Combine with `watch` for real-time:
```bash
watch -n 1 'df -h'
```
- Use `grep`, `less`, and `awk` to filter output

---

## 📦 Recommended Tools to Install
```bash
sudo apt install htop iotop dstat nmap net-tools sysstat -y
