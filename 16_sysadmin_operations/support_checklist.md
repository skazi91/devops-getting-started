# 🧾 Support Checklist – Basic Linux Troubleshooting Flow

A helpful checklist for Tier 1/2 support teams, junior sysadmins, or anyone responsible for triaging Linux issues.

---

## 🔍 CPU / RAM / Load
```bash
uptime
htop
free -h
top -n1 | head -n 20
```

---

## 💾 Disk Space
```bash
df -h
lsblk
ncdu /
```

---

## 🌐 Network
```bash
ip a
ping 8.8.8.8
curl ifconfig.io
sudo ufw status
```

---

## 📂 Logs & Services
```bash
journalctl -p 3 -xb
systemctl list-units --failed
sudo tail -n 50 /var/log/syslog
```

---

## 🔧 Software & Updates
```bash
sudo apt update && sudo apt list --upgradable
sudo dpkg --configure -a
```

---

## 📡 Remote Access
Check SSH:
```bash
systemctl status ssh
sudo netstat -tulnp | grep ssh
```

---

## ✅ Checkpoints
- Are CPU/RAM/Disk near 100%?
- Is the network reachable?
- Are services running?
- Are there filesystem or boot errors?

---

## 🧠 Tips
- Don’t reboot blindly — check logs first
- Document issue, steps taken, and resolution
- Escalate with logs + outputs if unresolved

> 💬 Logs tell the truth. Outputs tell the story. Use both.
