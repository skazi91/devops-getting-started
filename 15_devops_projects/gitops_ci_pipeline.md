# 🚀 GitOps CI Pipeline – Auto Deploy from GitHub

This project automatically deploys updated code to your Raspberry Pi, VPS, or cloud server after every push to `main` using GitHub Actions.

---

## 🧰 Prerequisites
- A server with SSH access and Docker installed
- SSH key pair added to GitHub secrets (`SSH_KEY`, `SERVER_IP`, `SERVER_USER`)

---

## 📁 Project Structure
```
myapp/
├── docker-compose.yml
└── .github/workflows/deploy.yml
```

---

## 🐳 docker-compose.yml
```yaml
version: '3'
services:
  web:
    image: your-image:latest
    ports:
      - "80:80"
```

---

## 🤖 .github/workflows/deploy.yml
```yaml
name: Deploy App
on:
  push:
    branches: [main]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Deploy over SSH
        uses: appleboy/ssh-action@v0.1.7
        with:
          host: ${{ secrets.SERVER_IP }}
          username: ${{ secrets.SERVER_USER }}
          key: ${{ secrets.SSH_KEY }}
          script: |
            cd /home/${{ secrets.SERVER_USER }}/myapp
            git pull
            docker compose pull
            docker compose up -d
```

---

## ✅ Features
- Git push triggers deployment
- Server auto-updates Docker containers
- Works with any Linux server (even Raspberry Pi)

> 🧠 Bonus: add health checks and rollback logic for production use
