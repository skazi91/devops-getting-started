# 📈 Prometheus + Grafana Stack Setup (DevOps Monitoring)

This guide will help you set up a basic Prometheus + Grafana monitoring stack on a Linux server, Raspberry Pi, or VM.
Perfect for DevOps learners, homelabbers, and system monitoring fans.

---

## 🧰 Requirements
- Linux-based system (Ubuntu/Debian recommended)
- Docker + Docker Compose (optional but easier)

---

## 🐳 1. Use Docker Compose (Quick & Clean Setup)
Create a folder:
```bash
mkdir monitoring-stack && cd monitoring-stack
```
Create `docker-compose.yml`:
```yaml
version: '3'
services:
  prometheus:
    image: prom/prometheus
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml
    ports:
      - "9090:9090"

  grafana:
    image: grafana/grafana
    ports:
      - "3000:3000"
    volumes:
      - grafana-storage:/var/lib/grafana

volumes:
  grafana-storage:
```

---

## 🧠 2. Create Prometheus Config
Create `prometheus.yml` in the same folder:
```yaml
global:
  scrape_interval: 15s

scrape_configs:
  - job_name: 'prometheus'
    static_configs:
      - targets: ['localhost:9090']
```
You can add other targets later (e.g., Node Exporter).

---

## 🚀 3. Run the Stack
```bash
docker-compose up -d
```

- Grafana: http://localhost:3000  
  (Default login: `admin` / `admin`)
- Prometheus: http://localhost:9090

---

## 📦 4. Add Prometheus as a Grafana Data Source
- Login to Grafana
- Go to **Settings > Data Sources**
- Add **Prometheus** with URL: `http://prometheus:9090`

---

## 📊 5. Add a Dashboard
- Go to **Dashboards > Import**
- Use ID `1860` for a popular Node Exporter dashboard (if installed)

---

## 🧩 Bonus: Add Node Exporter
```bash
docker run -d -p 9100:9100 prom/node-exporter
```
Update `prometheus.yml`:
```yaml
  - job_name: 'node'
    static_configs:
      - targets: ['host.docker.internal:9100']
```
Then reload Prometheus config.

---

## 📚 Resources
- [Prometheus Docs](https://prometheus.io/docs/introduction/overview/)
- [Grafana Labs Docs](https://grafana.com/docs/)
- [Awesome Grafana Dashboards](https://grafana.com/grafana/dashboards/)

---

> 💡 Tip: For production, always use persistent storage and secure with auth & TLS.
