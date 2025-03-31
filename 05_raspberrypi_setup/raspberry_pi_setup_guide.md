# 🍓 Raspberry Pi Setup Guide

## 🧰 What You Need
- Raspberry Pi 4 (any RAM version)
- microSD card (16GB+ recommended)
- microSD card reader
- Power supply (USB-C, 5V 3A)
- Internet access (Ethernet or Wi-Fi)

---

## 🖥️ Flash the OS
### 1. Download Raspberry Pi Imager
- [https://www.raspberrypi.com/software/](https://www.raspberrypi.com/software/)

### 2. Flash OS to SD card
- Choose OS: `Raspberry Pi OS (Lite)` (for headless DevOps projects)
- Click ⚙️ (Advanced options):
  - Enable SSH
  - Set username & password
  - Configure Wi-Fi (if needed)

### 3. Boot It Up
- Insert SD card
- Plug in power and wait ~1 min

---

## 🌐 Find Your Pi’s IP Address
- Use your router’s DHCP client list
- Or run `ping raspberrypi.local`

---

## 🔐 Connect via SSH
```bash
ssh pi@raspberrypi.local
```
Or use the IP:
```bash
ssh pi@192.168.x.x
```

---

## 🛠️ First-Time Setup
```bash
sudo apt update && sudo apt upgrade -y
sudo raspi-config
```
- Change hostname
- Set timezone & locale
- Enable/disable interfaces (I2C, SPI, Camera, etc.)

---

## 🐍 Recommended Installs
```bash
sudo apt install git curl htop net-tools unzip vim -y
```

## 🐳 Optional Tools
- **Docker**:
```bash
curl -sSL https://get.docker.com | sh
sudo usermod -aG docker pi
```
- **Portainer**:
```bash
docker volume create portainer_data
docker run -d -p 9000:9000 --name portainer \
  --restart=always -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data portainer/portainer-ce
```

---

## 🔁 Reboot
```bash
sudo reboot
```

You’re now ready to start building and automating with your Raspberry Pi!
