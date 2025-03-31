# 🛠️ Useful Linux Scripts – Automate Daily Tasks

Simple but powerful Bash scripts to help with system maintenance, updates, monitoring, and troubleshooting. Perfect for your homelab or server.

---

## 🔄 1. Update & Upgrade System (Debian/Ubuntu)
```bash
#!/bin/bash
sudo apt update && sudo apt upgrade -y && sudo apt autoremove -y
echo "✅ System updated!"
```
Save as: `update.sh`, then:
```bash
chmod +x update.sh
./update.sh
```

---

## 📦 2. Check Disk Space + Large Files
```bash
#!/bin/bash
clear
df -h | grep '^/dev'
echo -e "\nLargest files in /home:"
sudo du -ah /home | sort -rh | head -n 10
```

---

## 📋 3. Generate System Info Report
```bash
#!/bin/bash
hostnamectl > system_report.txt
uptime >> system_report.txt
free -h >> system_report.txt
df -h >> system_report.txt
ip a >> system_report.txt
echo "📄 Saved system_report.txt"
```

---

## 🚀 4. Restart Hung Services
```bash
#!/bin/bash
SERVICES=(nginx apache2 sshd)
for svc in "${SERVICES[@]}"; do
  sudo systemctl restart $svc && echo "✅ Restarted $svc"
done
```

---

## 🧹 5. Clean Up Logs Older Than 7 Days
```bash
#!/bin/bash
sudo find /var/log -type f -mtime +7 -exec rm -f {} \;
echo "🧼 Old logs cleaned!"
```
> Automate with `cron` to run weekly

---

## 🔍 6. Monitor System Resources Every 10s
```bash
#!/bin/bash
watch -n 10 "echo CPU: && top -bn1 | grep 'Cpu' && echo Memory: && free -h"
```

---

## 📂 7. Backup Folder to External Drive
```bash
#!/bin/bash
SRC="/home/user/Documents"
DEST="/mnt/backup/"
rsync -av --delete "$SRC" "$DEST"
echo "✅ Backup complete."
```

---

## 🧠 Tips
- Always test scripts with `echo` first before adding `rm`, `systemctl`, etc.
- Use `cron` or `systemd timers` to schedule them
- Save reusable ones in `~/bin` and add it to `$PATH`

---

## ✅ Suggested Tools
| Tool | Use |
|------|-----|
| `bash` | Basic scripting |
| `cron` | Scheduling scripts |
| `rsync` | Sync/backup files |
| `logrotate` | Rotate and compress logs automatically |

> Want to share your own scripts? Open a PR and contribute!
