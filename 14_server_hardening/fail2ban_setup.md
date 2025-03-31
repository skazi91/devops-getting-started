# 🚫 Fail2Ban Setup – Block Brute-Force Attacks

Fail2Ban scans log files and bans IPs that show malicious signs — too many password failures, exploit scans, etc.

---

## 📦 Install Fail2Ban
```bash
sudo apt update
sudo apt install fail2ban -y
```

---

## 📝 Create Custom Config
Never edit the original `jail.conf`. Copy it instead:
```bash
sudo cp /etc/fail2ban/jail.conf /etc/fail2ban/jail.local
```
Edit:
```bash
sudo nano /etc/fail2ban/jail.local
```

---

## 🔧 Recommended SSH Jail
```ini
[sshd]
enabled = true
port    = ssh
logpath = %(sshd_log)s
maxretry = 3
findtime = 10m
bantime  = 1h
```

---

## ▶️ Start & Enable
```bash
sudo systemctl restart fail2ban
sudo systemctl enable fail2ban
```

---

## 🔍 Monitor Status
```bash
sudo fail2ban-client status
sudo fail2ban-client status sshd
```

---

## 📋 Unban an IP
```bash
sudo fail2ban-client set sshd unbanip 192.168.1.100
```

---

## 📚 Logs
```bash
cat /var/log/fail2ban.log
journalctl -u fail2ban
```

> 🧠 Bonus: Add jails for `nginx`, `apache`, `vsftpd`, and more
