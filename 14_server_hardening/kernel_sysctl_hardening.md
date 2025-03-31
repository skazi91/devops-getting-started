# 🧠 Kernel Sysctl Hardening – Secure the OS Core

Apply secure kernel-level settings via `/etc/sysctl.conf` to protect your system from common network attacks.

---

## 🛡️ Why Harden with Sysctl?
- Prevent IP spoofing
- Reduce surface area of TCP/IP stack
- Mitigate DoS attacks
- Apply sane security defaults

---

## 📜 Recommended Settings
Add to:
```bash
sudo nano /etc/sysctl.conf
```

### 🔒 Network Hardening
```conf
net.ipv4.ip_forward = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.all.accept_source_route = 0
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.all.log_martians = 1
net.ipv4.tcp_syncookies = 1
net.ipv4.conf.all.rp_filter = 1
```

### 🧼 IPv6 Hardening
```conf
net.ipv6.conf.all.accept_redirects = 0
net.ipv6.conf.all.accept_source_route = 0
```

Apply changes:
```bash
sudo sysctl -p
```

---

## 🧪 Check Settings
```bash
sysctl -a | grep martian
sysctl net.ipv4.conf.all.accept_redirects
```

---

## 📚 Resources
- [sysctl man page](https://man7.org/linux/man-pages/man8/sysctl.8.html)
- [CIS Benchmarks](https://www.cisecurity.org/cis-benchmarks/)
- Try audit tools like `lynis` or `cis-cat`
