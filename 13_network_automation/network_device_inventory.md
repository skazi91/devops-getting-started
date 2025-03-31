# 📋 Network Device Inventory (CSV/YAML Based)

Keep track of all your routers, switches, firewalls, and virtual devices with a structured inventory file. Ideal for use in Python automations and audits.

---

## 🧾 Example CSV Inventory
**devices.csv**
```csv
name,ip,type,username,password
mikrotik1,192.168.88.1,mikrotik,admin,pass123
cisco1,192.168.1.1,cisco,admin,cisco123
```

Read it in Python:
```python
import csv
with open("devices.csv") as f:
    reader = csv.DictReader(f)
    for device in reader:
        print(device["name"], device["ip"])
```

---

## 📘 Example YAML Inventory
**devices.yaml**
```yaml
mikrotik1:
  ip: 192.168.88.1
  type: mikrotik
  username: admin
  password: pass123

cisco1:
  ip: 192.168.1.1
  type: cisco
  username: admin
  password: cisco123
```

Read it in Python:
```python
import yaml
with open("devices.yaml") as f:
    devices = yaml.safe_load(f)
    for name, data in devices.items():
        print(name, data["ip"])
```

---

## ✅ Benefits
- Clean, readable, scriptable
- Integrates with Paramiko, Netmiko, Nornir
- Ideal for larger networks

> 🧠 Keep this version-controlled and password-safe with `.gitignore` or vaulting tools.
