# 📊 Log Forwarding + Dashboard – Central Logging Stack

Build a small log collection and dashboard system for your homelab or server fleet using rsyslog + Grafana + Loki.

---

## 🎯 What You’ll Build
- Collect logs from multiple systems via `rsyslog`
- Store logs with [Loki](https://grafana.com/oss/loki/)
- View logs with [Grafana](https://grafana.com/)

---

## 🧰 Tools Required
- Docker & Docker Compose
- rsyslog installed on clients

---

## 🐳 docker-compose.yml
```yaml
version: '3'
services:
  loki:
    image: grafana/loki:2.8.2
    ports: ["3100:3100"]
    volumes:
      - ./loki-config.yaml:/etc/loki/local-config.yaml

  promtail:
    image: grafana/promtail:2.8.2
    volumes:
      - /var/log:/var/log
      - ./promtail-config.yaml:/etc/promtail/config.yml

  grafana:
    image: grafana/grafana:latest
    ports: ["3000:3000"]
```

---

## 📤 Client (rsyslog) Setup
Edit `/etc/rsyslog.d/90-remote.conf`:
```bash
*.* @@192.168.1.10:514
```
Allow TCP/UDP 514 on your central server and verify logs are flowing.

---

## 🖥️ View in Grafana
- Default login: `admin/admin`
- Add Loki as a data source
- Build dashboards by hostname, app, priority

> 📡 Useful for monitoring routers, firewalls, RPi, and containers!
