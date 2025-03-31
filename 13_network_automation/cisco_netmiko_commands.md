# 🧠 Cisco Automation with Netmiko (Python)

Use Netmiko (built on Paramiko) to automate Cisco router/switch tasks with Python.

---

## 📦 Requirements
```bash
pip install netmiko
```

---

## 🔧 Connect to Cisco Router
```python
from netmiko import ConnectHandler

cisco = {
    "device_type": "cisco_ios",
    "ip": "192.168.1.1",
    "username": "admin",
    "password": "password"
}

net_connect = ConnectHandler(**cisco)
print(net_connect.find_prompt())
```

---

## 🧪 Run Show Command
```python
output = net_connect.send_command("show ip interface brief")
print(output)
```

---

## ⚙️ Run Config Commands
```python
config_cmds = [
    "hostname DevRouter",
    "interface GigabitEthernet0/1",
    "description Connected to LAN"
]
net_connect.send_config_set(config_cmds)
```

---

## 🔁 Automate for Multiple Devices
```python
devices = [cisco1, cisco2, ...]
for device in devices:
    conn = ConnectHandler(**device)
    print(conn.send_command("show version"))
```

---

## 🔐 Pro Tips
- Always confirm changes manually at first
- Use `enable_password` if your devices require it
- Save config after changes with:
```python
net_connect.save_config()
```

> 📘 Docs: https://ktbyers.github.io/netmiko/
