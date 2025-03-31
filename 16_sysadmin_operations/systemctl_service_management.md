# 🛠️ systemctl & Service Management – Master systemd

Learn how to control, create, and troubleshoot services with `systemctl`, the interface to `systemd`.

---

## ▶️ Common systemctl Commands
```bash
sudo systemctl start nginx.service
sudo systemctl stop nginx.service
sudo systemctl restart nginx
sudo systemctl status nginx
```

Enable on boot:
```bash
sudo systemctl enable nginx
```
Disable:
```bash
sudo systemctl disable nginx
```

List all services:
```bash
systemctl list-units --type=service
```

---

## 📜 Create a Custom .service File
Create a unit file:
```bash
sudo nano /etc/systemd/system/myjob.service
```

Example:
```ini
[Unit]
Description=Run my custom script at boot
After=network.target

[Service]
Type=simple
ExecStart=/usr/local/bin/my-script.sh
Restart=on-failure

[Install]
WantedBy=multi-user.target
```

Enable and run:
```bash
sudo systemctl daemon-reexec   # Reload systemd
sudo systemctl enable myjob
sudo systemctl start myjob
```

---

## 🧪 Debugging
```bash
journalctl -u myjob
```
Show recent logs:
```bash
journalctl -xe
```

---

> 🔍 All production-grade Linux servers rely on proper service control — know it well!
