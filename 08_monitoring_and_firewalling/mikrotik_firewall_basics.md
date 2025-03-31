# 🔥 MikroTik Firewall Basics (RouterOS)

Protect your MikroTik router with basic but effective firewall filter and NAT rules. Perfect for home labs, small networks, or beginner network engineers.

---

## 🎯 What You'll Learn
- Default rule structure
- How to allow, drop, and log traffic
- NAT masquerading
- Tips to avoid locking yourself out

---

## 📦 Default Chains
- `input`: traffic *to* the router (Winbox, SSH, DNS, etc.)
- `forward`: traffic *through* the router (between interfaces)
- `output`: traffic *from* the router itself

---

## 🛡️ Basic Protection Rules
### Drop Invalid Packets
```bash
/ip firewall filter add chain=input connection-state=invalid action=drop comment="Drop invalid"
```

### Accept Established and Related Connections
```bash
/ip firewall filter add chain=input connection-state=established,related action=accept comment="Accept established"
```

### Allow Local Admin Access (Winbox + SSH)
```bash
/ip firewall filter add chain=input protocol=tcp port=22,8291 src-address=192.168.88.0/24 action=accept comment="Allow admin access"
```

### Drop Everything Else to Router
```bash
/ip firewall filter add chain=input action=drop comment="Drop everything else"
```

---

## 🌐 NAT Masquerading (Enable Internet Sharing)
```bash
/ip firewall nat add chain=srcnat out-interface=ether1 action=masquerade comment="NAT for Internet"
```
> Replace `ether1` with your WAN interface

---

## 🔍 View & Manage Rules
```bash
/ip firewall filter print
/ip firewall nat print
```
You can also remove rules by number:
```bash
/ip firewall filter remove [find where comment="Drop everything else"]
```

---

## 📢 Pro Tips
- Put rules in order: top-down evaluation
- Always allow Winbox or SSH *from your trusted subnet* before dropping all input!
- Use `/log print` to view log entries (e.g., log dropped connections)

---

## 🔗 Resources
- [MikroTik Docs: Firewall](https://help.mikrotik.com/docs/display/ROS/Firewall)
- [YouTube: MikroTik Firewall Explained](https://www.youtube.com/results?search_query=mikrotik+firewall+basics)
