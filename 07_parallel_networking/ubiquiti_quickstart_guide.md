# 📡 Ubiquiti (UniFi) Quickstart Guide

## 🧰 Products This Applies To
- UniFi Dream Machine (UDM/UDM-Pro)
- UniFi Security Gateway (USG)
- UniFi Switches & Access Points

---

## 🛠️ Controller Access
- Install **UniFi Controller Software** on a PC, Raspberry Pi, or use a Cloud Key
- Or use the **UniFi Network App** (iOS/Android)
- Login via: `https://<controller-ip>:8443`

---

## 🧾 Initial Setup
1. Adopt devices from controller dashboard
2. Assign names and confirm firmware updates
3. Set up SSIDs under **Wi-Fi Settings**
4. Set VLANs under **Networks > Advanced**
5. Configure guest access and firewall rules

---

## 🔧 Common CLI Access (Advanced)
```bash
ssh ubnt@192.168.1.20
# default password: ubnt (change it after first login!)
```

### Change IP via CLI
```bash
configure
set interfaces ethernet eth0 address 192.168.1.10/24
commit
save
exit
```

---

## 🌐 Create a New VLAN
```bash
set interfaces ethernet eth1 vif 20 description VLAN20
set interfaces ethernet eth1 vif 20 address 192.168.20.1/24
commit
save
```

---

## 🔒 Add Firewall Rule (CLI)
```bash
set firewall name BLOCK_SSH rule 10 action drop
set firewall name BLOCK_SSH rule 10 destination port 22
set firewall name BLOCK_SSH rule 10 protocol tcp
commit
save
```

---

## 💡 Tips
- Use **site tagging** to organize multiple locations
- VLANs and subnets can be assigned per SSID
- Use **Remote Access** via unifi.ui.com for cloud management

---

## 📖 Resources
- [UniFi Help Center](https://help.ui.com/)
- [Community Forum](https://community.ui.com/)
