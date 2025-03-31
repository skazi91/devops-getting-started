# 📡 IoT Network Monitor with Netdata + Node Exporter

Monitor multiple Raspberry Pi or ESP32-based devices using open-source telemetry tools.

---

## 🧰 What You’ll Use
- [Netdata](https://www.netdata.cloud/) – real-time dashboard
- [Node Exporter](https://github.com/prometheus/node_exporter) – export Linux metrics
- Prometheus/Grafana (optional central dashboard)

---

## 🚀 Setup on Each IoT Device
```bash
curl -sSL https://get.netdata.cloud | sudo bash
```
Or for Node Exporter:
```bash
wget https://github.com/prometheus/node_exporter/releases/latest/...tar.gz
./node_exporter &
```

---

## 🖥️ Central Dashboard (Optional)
Install Prometheus and Grafana on your homelab server.

- Configure Prometheus to scrape IoT metrics:
```yaml
scrape_configs:
  - job_name: 'iot-nodes'
    static_configs:
      - targets: ['192.168.1.101:9100', '192.168.1.102:9100']
```
- Visualize in Grafana

---

## 🔐 Network Tips
- Use Tailscale to isolate IoT from internet
- Send metrics through a secure VPN overlay

> 📟 This setup scales from 1 device to 100 — without paid tools!
