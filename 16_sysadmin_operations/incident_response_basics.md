# 🚨 Incident Response Basics – What to Do When It Breaks

This guide provides a step-by-step playbook for Linux system admins when things go wrong.

---

## 📟 Step 1: Identify the Problem
```bash
uptime             # Load average and uptime
free -h            # RAM usage
df -h              # Disk space
```
Check logs:
```bash
journalctl -p 3 -xb   # Critical logs
```

---

## 🔌 Step 2: Check Services
```bash
systemctl list-units --failed
systemctl status nginx
```
Restart a service:
```bash
sudo systemctl restart sshd
```

---

## 📡 Step 3: Check Network
```bash
ping 8.8.8.8
ip a
ip r
```
Check firewall:
```bash
sudo ufw status
```

---

## 🧱 Step 4: Stop the Bleed
- Disable crashing service:
```bash
sudo systemctl stop crashing.service
```
- Isolate the server from public:
```bash
sudo iptables -A INPUT -s 0.0.0.0/0 -j DROP
```

---

## 🧯 Step 5: Backup & Document
Before you reboot:
```bash
tar -czf logs_backup.tar.gz /var/log
cp -r /etc /root/config_backup/
```
Keep a changelog or incident journal:
```
what happened, what was affected, what you did
```

---

## ✅ Step 6: Recover or Reboot
- Revert recent changes if config-related
- Restore from backup if needed
- Only reboot as last resort (after backup!)

---

> 🧠 Stay calm. Start from known good. Logs are your best friends.
