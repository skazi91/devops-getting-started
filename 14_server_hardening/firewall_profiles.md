# 🔥 Firewall Profiles – Use Case Templates (UFW / iptables)

Create and reuse simple firewall rule sets for common server types. This guide focuses on `ufw` (easy mode) and `iptables` (advanced mode).

---

## 🌐 Web Server (HTTP/HTTPS Only)
### UFW
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw enable
```

### iptables
```bash
iptables -P INPUT DROP
iptables -A INPUT -p tcp --dport 80 -j ACCEPT
iptables -A INPUT -p tcp --dport 443 -j ACCEPT
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
```

---

## 🧑‍💻 SSH-Only Server (Remote Admin)
```bash
ufw allow OpenSSH
ufw limit OpenSSH
ufw enable
```

Or restrict by IP:
```bash
ufw allow from 192.168.1.10 to any port 22 proto tcp
```

---

## 📡 Monitoring Server (Custom Port)
Example: Netdata on 19999
```bash
ufw allow 19999/tcp
```

---

## 🔒 Hardened VPS Profile
- Allow only:
  - SSH (from 1 IP or subnet)
  - HTTPS
  - Fail2Ban and UFW combo
- Drop invalid packets:
```bash
iptables -A INPUT -m conntrack --ctstate INVALID -j DROP
```

---

## 📚 Tips
- Always test before `ufw enable`
- Save `iptables` rules:
```bash
iptables-save > /etc/iptables/rules.v4
```
- Log dropped packets:
```bash
iptables -A INPUT -j LOG --log-prefix "[IPTABLES DROP] " --log-level 4
```

> 🚨 Don’t lock yourself out! Keep a second SSH session open during tests.
