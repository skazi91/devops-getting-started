# 📁 09_backup_and_recovery

## 💾 Automated Backups for Homelab & DevOps Environments

Protect your configs, files, and environments with these beginner-friendly backup methods. From cron jobs to tools like `rsync`, this guide will help you keep your setups safe.

---

## 🧰 What You’ll Learn
- Basic Linux backup commands
- How to schedule cron jobs
- Backup Docker volumes
- MikroTik config backup
- Optional tools: `rsync`, `Restic`, `BorgBackup`

---

## 🗃️ 1. Backup Files with `rsync`
```bash
rsync -av --delete /home/pi/projects/ /mnt/backup/projects_backup/
```
- `-a`: archive mode
- `-v`: verbose
- `--delete`: remove files from destination if they no longer exist in source

---

## ⏰ 2. Automate with `cron`
### Edit crontab:
```bash
crontab -e
```
### Schedule daily 2am backup:
```cron
0 2 * * * rsync -av /home/pi/important/ /mnt/backup/important/
```

---

## 🐳 3. Backup Docker Volumes
```bash
docker run --rm \
  -v your_volume:/volume \
  -v $(pwd):/backup \
  alpine \
  tar czf /backup/volume_backup.tar.gz -C /volume .
```
To restore:
```bash
tar xzf volume_backup.tar.gz -C /some/new/volume
```

---

## 📦 4. MikroTik Backup (via CLI)
### Manual:
```bash
/system backup save name=router_backup
```
### Export config:
```bash
/export file=full_config
```
### Automate with script (schedule it!):
```bash
/system script add name=auto_backup policy=ftp,read,write,test source="/system backup save name=scheduled"
/system scheduler add name=weekly_backup interval=7d on-event=auto_backup
```

---

## 📚 Bonus Tools
| Tool | Description |
|------|-------------|
| `rsync` | Fast file copy & sync tool |
| `Restic` | Modern encrypted backup CLI (supports cloud too) |
| `BorgBackup` | Deduplicated and compressed backups |
| `Duplicati` | GUI backup manager for Linux/Windows |

---

## 🔐 Security Tips
- Always encrypt backups that leave your network
- Use versioned folders or timestamps to avoid overwriting
- Test your backups regularly!

---

## 🌐 References
- [rsync Tutorial](https://linux.die.net/man/1/rsync)
- [Restic Backup](https://restic.net/)
- [MikroTik Backup Docs](https://help.mikrotik.com/docs/display/ROS/Backup)
