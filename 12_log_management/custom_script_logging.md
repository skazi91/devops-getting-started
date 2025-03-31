# 📝 Logging in Your Own Scripts (Bash + Python)

Learn how to add helpful logs to your own scripts for easier debugging, auditing, and DevOps automation visibility.

---

## 🧰 Why Add Logging?
- See what's running and when
- Track errors and outputs
- Forward script output to log files or syslog

---

## 🧪 Bash Logging Example
```bash
#!/bin/bash
LOGFILE="/var/log/my_script.log"

log() {
  echo "$(date '+%Y-%m-%d %H:%M:%S') | $1" >> "$LOGFILE"
}

log "Script started"
# Run a command and log it
if ping -c 1 8.8.8.8 > /dev/null; then
  log "Internet connection OK"
else
  log "Internet check failed"
fi
log "Script ended"
```
> Make sure `/var/log/my_script.log` is writable or use your home dir.

---

## 📤 Bash: Send to Syslog
```bash
echo "Deployment started" | logger -t deploy-script
```
This will appear in `/var/log/syslog` or via `journalctl -t deploy-script`

---

## 🐍 Python Logging Example
```python
import logging

logging.basicConfig(
    filename='/var/log/myscript.log',
    level=logging.INFO,
    format='%(asctime)s %(levelname)s: %(message)s'
)

logging.info("Script started")
try:
    result = 1 / 0  # example error
except Exception as e:
    logging.error(f"Error occurred: {e}")
logging.info("Script ended")
```

---

## 🔁 Rotate Script Logs
Add your script logs to `/etc/logrotate.d/` for cleanup and archiving.
```bash
/var/log/myscript.log {
  weekly
  rotate 4
  compress
  missingok
  notifempty
}
```

---

## 📦 Logging Best Practices
- Always include timestamps
- Log at levels: INFO, WARNING, ERROR, DEBUG
- Separate logs by function or module if needed
- Store logs securely or forward to a collector

---

## 🧠 Bonus Tip
Wrap scripts with global trap logging:
```bash
trap 'echo "Script failed on line $LINENO" | logger -t error-trap' ERR
```

> 💡 Logging isn't just for big servers — it's for every script you’ll maintain later!
