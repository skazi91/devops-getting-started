# 🕒 Cron & Scheduled Tasks – Automate Everything

Learn how to run scripts, backups, health checks, and cleanup jobs on a schedule using `cron`, `systemd timers`, and `at`.

---

## 🧭 Cron Basics
Edit your user’s crontab:
```bash
crontab -e
```

Format:
```
* * * * * command-to-run
| | | | |
| | | | +----- Day of week (0-7)
| | | +------- Month (1-12)
| | +--------- Day of month (1-31)
| +----------- Hour (0-23)
+------------- Minute (0-59)
```

### 🔁 Examples
- Run every day at 2 AM:
  ```cron
  0 2 * * * /home/user/backup.sh
  ```
- Run every 5 minutes:
  ```cron
  */5 * * * * /home/user/ping-check.sh
  ```

---

## 📁 System-Wide Cron
System-wide config lives in:
```bash
/etc/crontab
/etc/cron.daily/
/etc/cron.hourly/
```

---

## 🧪 Log Cron Output
Redirect output in your cron jobs:
```cron
0 1 * * * /path/to/script.sh >> /var/log/mycron.log 2>&1
```

---

## 🔁 Systemd Timers (Alternative to Cron)
Timers offer better logging and dependencies.

### Example: `/etc/systemd/system/cleanup.timer`
```ini
[Unit]
Description=Daily cleanup

[Timer]
OnCalendar=daily
Persistent=true

[Install]
WantedBy=timers.target
```

### Paired with: `cleanup.service`
```ini
[Service]
ExecStart=/usr/local/bin/cleanup.sh
```

Enable both:
```bash
sudo systemctl enable --now cleanup.timer
```

---

## 🔂 Run Once Later (with `at`)
```bash
sudo apt install at
at now + 1 hour
> /home/user/script.sh
```
List scheduled:
```bash
atq
```

---

## ✅ Use Cases
- Log rotation or compression
- System health report
- Auto-reboot recovery
- Offline backup jobs

> 🧠 Cron is your low-resource automation scheduler. Use it wisely!
