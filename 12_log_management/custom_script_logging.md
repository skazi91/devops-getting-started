# ✍️ Logging in Your Own Scripts (Bash & Python)

Learn how to add simple, structured logging to your Bash and Python scripts for better debugging, monitoring, and log forwarding.

---

## 🧾 Bash Script Logging

### 📜 Example
```bash
#!/bin/bash
LOGFILE="/var/log/myscript.log"
log() {
  echo "[$(date +'%Y-%m-%d %H:%M:%S')] $1" | tee -a "$LOGFILE"
}

log "Script started."
# Do something
log "Completed task."
```

---

### 🔧 Tips for Bash Logging
- Use `logger` to send messages to system journal:
```bash
echo "Backup started" | logger -t backup-script
```
- Combine with `rsyslog` to forward custom script logs

---

## 🐍 Python Script Logging

### 🔧 Built-in Logging Module
```python
import logging
logging.basicConfig(filename='/var/log/myscript.log', level=logging.INFO,
                    format='%(asctime)s [%(levelname)s] %(message)s')

logging.info("Script started")
logging.warning("This is a warning")
logging.error("Something went wrong")
```

### 📤 Send to syslog (Optional)
```python
import logging.handlers
syslog = logging.handlers.SysLogHandler(address='/dev/log')
logger = logging.getLogger()
logger.addHandler(syslog)
logger.warning("This goes to syslog")
```

---

## 📦 Rotating Script Logs
Make sure logs don’t grow endlessly:
```bash
sudo nano /etc/logrotate.d/myscript
```
```conf
/var/log/myscript.log {
  weekly
  rotate 4
  compress
  missingok
  notifempty
}
```

---

## 🧠 Best Practices
- Log at multiple levels (INFO, WARNING, ERROR)
- Include timestamps
- Use consistent formats
- Rotate logs to avoid disk issues

---

## ✅ Use Cases
- Backup scripts
- Cron jobs
- Health checks
- Home automation

> 🧩 Logging transforms a one-off script into a production-grade tool.
