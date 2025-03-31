# 🔌 Cisco IOS Quickstart Guide

## 🖥️ Access Methods
- **Console cable** (via USB to Serial)
- **Telnet/SSH** (must be enabled)
```bash
ssh admin@192.168.1.1
```

---

## 🧾 Basic Setup Commands
```bash
enable
configure terminal
hostname MyRouter
enable secret StrongPass123
```

## 🌐 Set Interface IP
```bash
interface GigabitEthernet0/1
ip address 192.168.1.1 255.255.255.0
no shutdown
```

## 🔄 Create VLAN
```bash
vlan 10
name Admin
exit
interface FastEthernet0/1
switchport mode access
switchport access vlan 10
```

## 📡 Enable DHCP Server
```bash
ip dhcp pool LAN
network 192.168.10.0 255.255.255.0
default-router 192.168.10.1
dns-server 8.8.8.8
```

## 🔐 Configure SSH Access
```bash
ip domain-name mynetwork.local
crypto key generate rsa
ip ssh version 2
username admin privilege 15 secret mypassword
line vty 0 4
login local
transport input ssh
```

---

## 💾 Save Configuration
```bash
copy running-config startup-config
```

## 💡 Tips
- Use `?` for command hints
- Use `show running-config` to view active settings
- Use `write memory` as shortcut for saving

---

## 📖 Resources
- [Cisco Config Guides](https://www.cisco.com/c/en/us/support/index.html)
- [Packet Tracer Lab Practice](https://www.netacad.com/)
