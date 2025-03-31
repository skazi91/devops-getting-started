# 👥 User, Group & Permission Management – Linux Access Control

Control who can access, execute, and modify files on your system. Essential for secure server environments.

---

## 👤 Add & Manage Users
```bash
sudo adduser newuser
sudo passwd newuser
sudo userdel olduser
```

## 👥 Add to Groups
```bash
sudo usermod -aG sudo newuser   # Give sudo access
sudo groups newuser
```

### 🛠 Common Groups
- `sudo`: root-like access
- `www-data`: web services (e.g. nginx)
- `docker`: run Docker without `sudo`

---

## 📂 File Permissions Cheat Sheet
```bash
ls -l                # View permissions
chmod 755 file       # Change permission (rwxr-xr-x)
chown user:group file  # Change owner & group
```

### 🔢 Numeric Permissions
| Mode | Meaning        |
|------|----------------|
| 7    | rwx            |
| 6    | rw-            |
| 5    | r-x            |
| 4    | r--            |
| 0    | ---            |

Example:
```bash
chmod 644 index.html   # rw-r--r--
```

---

## 📁 Directory Ownership
```bash
chown -R myuser:mygroup /var/www/html
```

To allow shared group access:
```bash
chmod g+s /project/folder
```

---

## 🔒 Security Tips
- Never use 777 unless testing
- Use `umask 027` for secure default perms
- Check for world-writable files:
```bash
find / -type f -perm -0002
```

> 🧠 Mastering permissions = mastering system safety.
