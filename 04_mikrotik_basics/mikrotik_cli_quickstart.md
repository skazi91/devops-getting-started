# 🛜 MikroTik RouterOS CLI Quickstart Guide

## 🔑 Accessing MikroTik CLI
### WinBox (GUI)
- Download from: [https://mikrotik.com/download](https://mikrotik.com/download)
- Connect using MAC or IP address

### Terminal or SSH
```bash
ssh admin@192.168.88.1
```

---

## 📦 Basic Setup Commands
```bash
/system identity set name="MyRouter"
/user set admin password="StrongPass123"
```

## 🌐 Set IP Address
```bash
/ip address add address=192.168.1.1/24 interface=ether1
```

## 🚪 Enable DHCP Server
```bash
/ip dhcp-server setup
```

## 🔒 Basic Firewall Rule Example
```bash
/ip firewall filter add chain=input protocol=tcp dst-port=22 action=drop comment="Block SSH from outside"
```

## 📡 Wireless Setup (for Wi-Fi models)
```bash
/interface wireless set wlan1 ssid="MyWiFi" disabled=no
```

## 🔄 NAT Masquerade (For Internet Sharing)
```bash
/ip firewall nat add chain=srcnat action=masquerade out-interface=ether1
```

---

## 🧼 Backup & Restore
```bash
/system backup save name=mybackup
/system backup load name=mybackup.backup
```

## 💡 Tips
- Use `?` to show possible commands at any point
- Use tab to auto-complete
- Use `/` to jump back to root command

---

## 📖 Docs & Resources
- [RouterOS Documentation](https://help.mikrotik.com/docs/)
- [MikroTik Wiki](https://wiki.mikrotik.com/)
