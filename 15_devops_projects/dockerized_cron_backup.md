# 📦 Dockerized Cron Backup – Files to Volume or S3

A minimal container that runs a cron job to back up a directory every X hours. You can write to a mounted volume or sync to S3.

---

## 🧾 Folder Structure
```bash
cron-backup/
├── backup.sh
├── crontab.txt
├── Dockerfile
└── README.md
```

---

## 🐚 `backup.sh`
```bash
#!/bin/bash
TIMESTAMP=$(date +"%Y%m%d_%H%M%S")
tar -czf /backup/mydata_$TIMESTAMP.tar.gz /data
```

---

## 🕒 `crontab.txt`
```cron
0 */6 * * * /backup.sh >> /var/log/cron.log 2>&1
```

---

## 🐳 Dockerfile
```Dockerfile
FROM alpine
RUN apk add --no-cache bash tar curl
COPY backup.sh /backup.sh
COPY crontab.txt /crontab.txt
RUN chmod +x /backup.sh
CMD crond -f -l 8 -L /var/log/cron.log -c /crontab.txt
```

---

## 🚀 Run It
```bash
docker build -t cron-backup .
docker run -v $(pwd)/data:/data -v $(pwd)/backup:/backup cron-backup
```

---

## ☁️ Optional: Push to S3
Append to `backup.sh`:
```bash
aws s3 cp /backup/*.tar.gz s3://your-bucket/backups/ --recursive
```

> 🎯 Use this to automate local or cloud file backups in a fully isolated way.
