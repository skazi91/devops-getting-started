# 🔐 SSH Automation Basics (Bash + Python)

Automate repetitive SSH tasks using scripts — useful for managing servers, routers, switches, or any SSH-enabled device.

---

## 🧰 Option 1: Bash Script (Simple)
```bash
#!/bin/bash
HOST="192.168.88.1"
USER="admin"
CMD="/system resource print"

ssh ${USER}@${HOST} "$CMD"
```
> Add `-o StrictHostKeyChecking=no` if running in automation

---

## 🧰 Option 2: Python + Paramiko
Install first:
```bash
pip install paramiko
```
Example script:
```python
import paramiko
host = "192.168.88.1"
user = "admin"
password = "password"

client = paramiko.SSHClient()
client.set_missing_host_key_policy(paramiko.AutoAddPolicy())
client.connect(hostname=host, username=user, password=password)

stdin, stdout, stderr = client.exec_command("/system identity print")
print(stdout.read().decode())
client.close()
```

---

## 🧪 Add to Cron or Loop
Use cron to automate at intervals or a loop to run against multiple devices.

```bash
for host in 192.168.88.{1..5}; do
  ssh admin@$host "/interface print"
done
```

---

## ✅ Next Step
Use Paramiko or Netmiko to build reusable tools and scripts across networks!
