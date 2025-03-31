# 🔐 Basic Linux Firewall Rules (UFW & iptables)

A practical guide for beginners to secure Linux systems using simple firewall rules.

---

## ✅ Option 1: UFW (Uncomplicated Firewall)
UFW is great for quick and easy firewall management.

### 🛠️ Install and Enable
```bash
sudo apt install ufw -y
sudo ufw enable
```

### 🚪 Allow Common Services
```bash
sudo ufw allow ssh
sudo ufw allow 80/tcp   # HTTP
sudo ufw allow 443/tcp  # HTTPS
```

### ❌ Deny or Remove Access
```bash
sudo ufw deny 23         # Block Telnet
sudo ufw delete allow ssh  # Remove SSH access
```

### 🔍 Status and Logs
```bash
sudo ufw status numbered
sudo ufw status verbose
sudo less /var/log/ufw.log
```

---

## 🔥 Option 2: iptables (Advanced, Flexible)

### 🧱 Basic Commands
```bash
sudo iptables -L -v      # List all rules
sudo iptables -F         # Flush all rules (be careful!)
sudo iptables -X         # Delete all custom chains
```

### 🔐 Sample Rules
```bash
# Accept all from localhost
sudo iptables -A INPUT -i lo -j ACCEPT

# Allow SSH
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT

# Allow HTTP/HTTPS
sudo iptables -A INPUT -p tcp -m multiport --dports 80,443 -j ACCEPT

# Drop all other incoming traffic
sudo iptables -A INPUT -j DROP
```

### 💾 Save Rules (Debian/Ubuntu)
```bash
sudo apt install iptables-persistent
sudo netfilter-persistent save
```

---

## 🔄 Reset to Defaults
### UFW:
```bash
sudo ufw reset
```
### iptables:
```bash
sudo iptables -F
```

---

## ⚠️ Safety Tip
Always test your rules on a remote server using a second open SSH session, so you don’t lock yourself out!

---

## 📚 More Reading
- [UFW Docs](https://help.ubuntu.com/community/UFW)
- [iptables Tutorial](https://wiki.archlinux.org/title/Iptables)
