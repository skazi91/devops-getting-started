# 🔐 Secure SSH Config – Lock Down Remote Access

Learn how to harden your SSH server to prevent unauthorized access and brute-force attacks.

---

## 🧰 SSH Server Config File
Edit:
```bash
sudo nano /etc/ssh/sshd_config
```

---

## 🔧 Recommended Secure Settings
```conf
Port 22                  # (optional: change to custom port like 2222)
PermitRootLogin no
PasswordAuthentication no
ChallengeResponseAuthentication no
UsePAM yes
X11Forwarding no
PermitEmptyPasswords no
AllowUsers youradminuser
LoginGraceTime 30
ClientAliveInterval 300
ClientAliveCountMax 2
```

Then restart SSH:
```bash
sudo systemctl restart sshd
```

---

## 🛡️ SSH Key Authentication
On your client:
```bash
ssh-keygen -t ed25519
ssh-copy-id youruser@your.server.ip
```

---

## 🧪 Test Before Lockout!
Before closing your session:
```bash
ssh youruser@your.server.ip -p 22
```
Test login works with key only. Keep a backup session open.

---

## 📚 Bonus
- Use Fail2ban to block failed attempts
- Enable MFA with `pam_google_authenticator`
- Log SSH events:
```bash
journalctl -u sshd
```

> 🚧 Changing SSH settings on a remote server? Test in a screen/tmux session so you don’t get locked out!
