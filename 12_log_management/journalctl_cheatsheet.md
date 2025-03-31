# 📘 journalctl Cheat Sheet – systemd Log Explorer

`journalctl` is a powerful CLI tool for reading and filtering logs managed by `systemd` on most modern Linux distributions (Debian, Ubuntu, CentOS, Arch, etc).

---

## 🧪 Basic Usage
```bash
journalctl           # View full system log (oldest first)
journalctl -r        # Show newest entries first
journalctl -f        # Live follow (like tail -f)
```

---

## 📅 Filter by Time
```bash
journalctl --since today
journalctl --since "2024-04-01 12:00" --until "2024-04-01 13:00"
journalctl --since yesterday
```

---

## 🧩 Filter by Service/Unit
```bash
journalctl -u ssh.service          # Only SSH logs
journalctl -u nginx -u docker      # Multiple services
```
You can find service names with:
```bash
systemctl list-units --type=service
```

---

## 🔍 Search with Keywords
```bash
journalctl | grep 'error'
journalctl -u nginx | grep 403
```

---

## 📦 Show Boot Logs
```bash
journalctl -b           # Current boot
journalctl -b -1        # Previous boot
journalctl --list-boots # All boots with index
```

---

## 🧠 Extra Options
```bash
journalctl -n 50         # Last 50 lines
journalctl -p warning    # Only warnings or higher (see priority levels below)
journalctl -o short-iso  # Better timestamp format
```

---

## 🔐 Priority Levels (Severities)
| Code | Name    |
|------|---------|
| 0    | emerg   |
| 1    | alert   |
| 2    | crit    |
| 3    | err     |
| 4    | warning |
| 5    | notice  |
| 6    | info    |
| 7    | debug   |

Example:
```bash
journalctl -p 3 -b   # Errors since boot
```

---

## 🔐 Permissions & Security
- You may need `sudo` to read full logs
- All logs are stored in binary format under:
```bash
/var/log/journal/
```

---

## 📚 Resources
- [man journalctl](https://man7.org/linux/man-pages/man1/journalctl.1.html)
- [systemd logs](https://www.freedesktop.org/software/systemd/man/systemd-journald.service.html)

> 🧠 Pro tip: Use `journalctl -xef` to troubleshoot services live with context.
