# 👤 User & Sudo Policy – Minimal Privilege Setup

Lock down your system by enforcing a secure user and sudo access model. Avoid `root` usage and restrict administrative access.

---

## 👥 Step 1: Add a New User
```bash
sudo adduser devopsuser
sudo usermod -aG sudo devopsuser
```

---

## 🛑 Step 2: Disable Root Login
Edit SSH config:
```bash
sudo nano /etc/ssh/sshd_config
PermitRootLogin no
```
Then restart:
```bash
sudo systemctl restart sshd
```

---

## 🔒 Step 3: Use Sudo Restrictions
Edit sudoers:
```bash
sudo visudo
```

Grant access to only specific commands:
```bash
devopsuser ALL=(ALL) NOPASSWD: /usr/bin/systemctl restart nginx
```

Or restrict all but allow group:
```bash
%devopsadmins ALL=(ALL:ALL) ALL
```

---

## 📂 Step 4: Audit and Clean Up
```bash
sudo cat /etc/passwd | grep '/home'
sudo cat /etc/group | grep sudo
sudo lastlog | grep -v "Never"
```
Delete unused users:
```bash
sudo deluser olduser
sudo rm -rf /home/olduser
```

---

## ✅ Best Practices
- Use strong passwords or SSH keys only
- Rotate accounts regularly
- Avoid `sudo su` or full root access unless needed
- Use 2FA where possible (e.g., Google Authenticator)

> 🧠 Tip: Every system compromise begins with an overly privileged user.
