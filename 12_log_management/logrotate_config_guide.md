# 🔁 Logrotate Configuration Guide – Automate Log Cleanup

`logrotate` is a system utility that automatically rotates, compresses, and deletes old log files. This prevents your `/var/log` from filling up and helps manage long-term logs efficiently.

---

## 📦 What It Does
- Moves logs to `.1`, `.2.gz`, `.3.gz` etc.
- Compresses old logs
- Deletes logs after a defined retention period
- Restarts services if needed after log rotation

---

## 🧰 Default Location
```bash
/etc/logrotate.conf           # Main config file
/etc/logrotate.d/             # App-specific rules (e.g., nginx, apt)
```

---

## 📝 Sample Config Snippet
```bash
/var/log/syslog {
  daily
  missingok
  rotate 7
  compress
  delaycompress
  notifempty
  create 0640 syslog adm
  postrotate
    /usr/lib/rsyslog/rsyslog-rotate
  endscript
}
```
### What This Means:
- `daily`: Rotate log daily
- `rotate 7`: Keep 7 copies
- `compress`: Use gzip for older logs
- `notifempty`: Don’t rotate if empty
- `postrotate`: Run a script after rotation

---

## 🧪 Test Your Config
```bash
sudo logrotate -d /etc/logrotate.conf   # Dry run
sudo logrotate -f /etc/logrotate.conf   # Force rotation now
```

---

## 🔁 Cron Automation
Logrotate is usually run daily via cron:
```bash
cat /etc/cron.daily/logrotate
```
You don’t need to schedule it manually unless using a custom script.

---

## 📂 Add Custom Rule (Example)
To rotate a custom app log (e.g., `/var/log/myapp.log`):
1. Create config:
```bash
sudo nano /etc/logrotate.d/myapp
```
2. Add:
```bash
/var/log/myapp.log {
  weekly
  rotate 4
  compress
  missingok
  notifempty
}
```

---

## 📚 Resources
- [man logrotate](https://man7.org/linux/man-pages/man8/logrotate.8.html)
- `/etc/logrotate.conf` (read + experiment!)

> 💡 Use `delaycompress` to avoid compressing logs still in use.
