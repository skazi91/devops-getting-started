# 📊 Netdata Setup Guide (Real-Time Monitoring)

**Netdata** is a powerful, lightweight, and real-time monitoring tool with a beautiful web interface. It’s perfect for homelabs, Raspberry Pi, and production servers.

---

## ✅ Why Use Netdata?
- Real-time performance metrics
- Zero configuration for most services
- Visual dashboards for CPU, RAM, network, disk, apps, and more

---

## 🧰 Requirements
- Debian/Ubuntu/Raspberry Pi OS or similar Linux distro
- Internet connection

---

## ⚙️ 1. Install Netdata (Recommended Method)
### Run this one-liner:
```bash
bash <(curl -Ss https://my-netdata.io/kickstart.sh)
```
> It detects your OS and installs all dependencies automatically.

For Raspberry Pi, it's fully supported!

---

## 🌐 2. Access the Web UI
After installation, open your browser:
```http
http://<your-server-ip>:19999
```
Example:
```
http://192.168.1.10:19999
```

No login required by default (you can secure it later).

---

## 🛠️ 3. Start/Stop/Restart Netdata
```bash
sudo systemctl start netdata
sudo systemctl stop netdata
sudo systemctl restart netdata
sudo systemctl enable netdata
```

---

## 🔐 Optional: Secure Access (with NGINX Reverse Proxy)
You can place Netdata behind a reverse proxy like NGINX with HTTPS and authentication.

Example NGINX config snippet:
```nginx
location /netdata/ {
  proxy_pass http://localhost:19999/;
  proxy_set_header Host $host;
  proxy_http_version 1.1;
  proxy_set_header Upgrade $http_upgrade;
  proxy_set_header Connection "upgrade";
}
```

---

## 📈 What You Can Monitor
- CPU, RAM, swap
- Disk I/O, usage, SMART
- Network bandwidth, errors
- Running services: MySQL, NGINX, Docker, etc.

---

## 💾 Uninstall Netdata
```bash
sudo /usr/libexec/netdata-uninstaller.sh --yes
```

---

## 📚 Resources
- [Netdata Website](https://www.netdata.cloud/)
- [Netdata GitHub](https://github.com/netdata/netdata)
- [Community Docs](https://learn.netdata.cloud/docs/overview)
