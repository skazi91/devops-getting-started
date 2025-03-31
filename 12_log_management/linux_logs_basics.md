# 📁 Linux Logs Basics – What, Where, and How

A foundational guide to understanding logs in Linux systems. Learn where logs are stored, what tools read them, and how to use logs to troubleshoot and monitor your system.

---

## 📍 Where Are Logs Stored?
Most logs live inside:
```bash
/var/log/
```
Common files:
| File | Description |
|------|-------------|
| `/var/log/syslog` | General system messages (Debian-based) |
| `/var/log/messages` | Similar to syslog (CentOS/RHEL) |
| `/var/log/auth.log` | Logins, sudo, SSH, and authentication |
| `/var/log/dmesg` | Kernel ring buffer (boot-time & hardware) |
| `/var/log/apt/` | Package management logs |
| `/var/log/nginx/` | Web server logs (if installed) |
| `/var/log/journal/` | Binary systemd logs (read via `journalctl`) |

---

## 🔎 View Logs Using CLI
```bash
sudo less /var/log/syslog
sudo tail -f /var/log/auth.log
```
> Use `grep`, `awk`, and `cut` to filter logs efficiently

Example:
```bash
grep 'sshd' /var/log/auth.log
```

---

## 🧠 Log Levels (RFC 5424)
| Level | Meaning |
|-------|---------|
| `emerg` | System is unusable |
| `alert` | Immediate action required |
| `crit` | Critical condition |
| `err` | Error condition |
| `warning` | Warning condition |
| `notice` | Normal but significant event |
| `info` | Informational message |
| `debug` | Debug-level message (verbose) |

---

## 📦 Applications That Log
- `systemd`, `rsyslog`, `journald`
- `nginx`, `apache2`, `fail2ban`, `ufw`
- `cron`, `docker`, `ssh`, `sudo`

---

## 🧪 Example: Track Failed SSH Logins
```bash
grep 'Failed password' /var/log/auth.log
```
Or with `journalctl`:
```bash
journalctl -u ssh --since today | grep Failed
```

---

## 🔐 Permissions Note
Some log files require `sudo` to read.
Always audit with care — logs may contain sensitive data (IPs, usernames, etc.)

---

## ✅ Next Step
Go deeper with:
- [`journalctl_cheatsheet.md`](./journalctl_cheatsheet.md)
- [`logrotate_config_guide.md`](./logrotate_config_guide.md)
