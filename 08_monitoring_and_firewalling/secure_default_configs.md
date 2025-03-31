# 🔐 Secure Default Configs for Linux Servers & Homelabs

This guide provides a checklist of essential security tweaks and configuration steps for any fresh Linux system (especially VPS, cloud servers, and Raspberry Pis).

---

## 🚫 1. Disable Root SSH Login
```bash
sudo nano /etc/ssh/sshd_config
```
Change or add:
```
PermitRootLogin no
PasswordAuthentication no
```
Then restart SSH:
```bash
sudo systemctl restart ssh
```

---

## 🔐 2. Create a New User with Sudo
```bash
sudo adduser youruser
sudo usermod -aG sudo youruser
```
Then login via SSH with your new user instead of `root`.

---

## 🔒 3. Enable the UFW Firewall
```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
sudo ufw allow ssh
sudo ufw enable
```

---

## 📅 4. Enable Automatic Security Updates
### For Debian/Ubuntu:
```bash
sudo apt install unattended-upgrades -y
sudo dpkg-reconfigure --priority=low unattended-upgrades
```
Logs:
```bash
cat /var/log/unattended-upgrades/unattended-upgrades.log
```

---

## 🧱 5. Disable Unused Services
Check what's running:
```bash
sudo systemctl list-units --type=service --state=running
```
Disable unnecessary services:
```bash
sudo systemctl disable bluetooth
sudo systemctl stop bluetooth
```

---

## 🧪 6. Install Basic Monitoring Tools
```bash
sudo apt install htop iotop fail2ban curl -y
```
Set up Fail2ban to block brute force:
```bash
sudo systemctl enable fail2ban
sudo systemctl start fail2ban
```

---

## 🔑 7. Use SSH Keys Instead of Passwords
On your client:
```bash
ssh-keygen -t rsa -b 4096 -C "you@example.com"
ssh-copy-id youruser@yourserver
```

---

## 🔄 8. Keep System Up to Date
```bash
sudo apt update && sudo apt upgrade -y
```
(Optional: set up `cron` or alias to do this weekly)

---

## 🧠 Bonus Tips
- Change default ports for SSH (`/etc/ssh/sshd_config`)
- Use a VPN for remote access if possible
- Configure a host-based intrusion detection tool (like `rkhunter`, `chkrootkit`, or `Wazuh`)

---

## 📚 References
- [Debian Hardening Guide](https://wiki.debian.org/Hardening)
- [Ubuntu Server Guide](https://ubuntu.com/server/docs)
