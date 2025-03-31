# 🤖 Automate MikroTik with Paramiko (Python)

Control and query MikroTik routers via SSH using Python and the Paramiko library.

---

## 🔧 Requirements
```bash
pip install paramiko
```
Ensure SSH is enabled on your MikroTik:
```bash
/ip service enable ssh
```

---

## 📋 Example: Fetch Router Identity
```python
import paramiko
router_ip = "192.168.88.1"
username = "admin"
password = "yourpass"

ssh = paramiko.SSHClient()
ssh.set_missing_host_key_policy(paramiko.AutoAddPolicy())
ssh.connect(router_ip, username=username, password=password)

stdin, stdout, stderr = ssh.exec_command("/system identity print")
print(stdout.read().decode())
ssh.close()
```

---

## 💾 Example: Backup MikroTik Config
```python
backup_cmd = "/system backup save name=remote-backup"
ssh.exec_command(backup_cmd)
```

---

## 🔁 Automate Across Inventory
```python
routers = ["192.168.88.1", "192.168.88.2"]
for ip in routers:
    ssh.connect(ip, username=username, password=password)
    stdin, stdout, stderr = ssh.exec_command("/interface print")
    print(stdout.read().decode())
    ssh.close()
```

---

## ✅ Bonus: Handle Output, Logs, or CSV
Save results to a file or log using Python’s `csv` or `logging` modules.

> 🛡️ Always test SSH scripts with `read-only` commands first!
