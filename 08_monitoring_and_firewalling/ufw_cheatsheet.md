# 🧱 UFW Cheat Sheet (Uncomplicated Firewall)

UFW is a simple command-line firewall frontend for iptables, perfect for beginners and Ubuntu/Debian systems.

---

## 🔧 Enable & Disable
```bash
sudo ufw enable      # Turn on firewall
sudo ufw disable     # Turn off firewall
sudo ufw reload      # Reload rules
```

---

## 🚪 Allow & Deny Services
```bash
sudo ufw allow ssh         # Allow SSH (default port 22)
sudo ufw allow 80/tcp      # Allow HTTP
sudo ufw allow 443/tcp     # Allow HTTPS
sudo ufw deny 23           # Block Telnet
```

### Port Ranges & IPs
```bash
sudo ufw allow 1000:2000/tcp
sudo ufw allow from 192.168.1.100
sudo ufw allow from 192.168.1.0/24 to any port 22
```

---

## 🔍 View Rules
```bash
sudo ufw status
sudo ufw status numbered
```

---

## ❌ Deleting Rules
```bash
sudo ufw delete allow ssh
sudo ufw delete 2    # Based on rule number
```

---

## 🔐 Default Policies (Secure Baseline)
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

---

## 🔄 Reset to Defaults
```bash
sudo ufw reset
```
> Warning: This deletes all rules!

---

## 🧪 Logging
```bash
sudo ufw logging on
sudo tail -f /var/log/ufw.log
```

---

## 🔗 Resources
- [UFW Docs](https://wiki.ubuntu.com/UncomplicatedFirewall)
- `man ufw` for built-in help
