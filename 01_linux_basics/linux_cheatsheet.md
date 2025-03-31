# 🐧 Linux Command Cheat Sheet

## 🔍 Navigation
- `pwd` – Show current directory
- `ls -lAh` – List files with permissions and human-readable sizes
- `cd ~/Downloads` – Change to Downloads folder

## 📁 File and Directory Operations
- `touch file.txt` – Create a file
- `mkdir myfolder` – Create folder
- `cp file.txt backup/` – Copy file
- `mv file.txt archive/` – Move file
- `rm file.txt` – Delete file
- `rm -rf folder/` – Delete folder recursively

## 🔐 Permissions and Ownership
- `chmod +x script.sh` – Make script executable
- `chown user:user file.txt` – Change ownership
- `ls -la` – Show permissions

## 🌐 Networking
- `ip a` – Show IP addresses
- `ping 8.8.8.8` – Ping a server
- `curl ifconfig.me` – Show external IP
- `netstat -tuln` – Show open ports
- `ss -tulnp` – Show listening sockets

## 🧠 System Info & Processes
- `top` or `htop` – View running processes
- `df -h` – Disk space usage
- `free -m` – RAM usage
- `uptime` – System load and uptime

## ⚙️ Package Management (Debian/Ubuntu)
- `sudo apt update` – Refresh package list
- `sudo apt upgrade` – Upgrade installed packages
- `sudo apt install nmap` – Install nmap
- `sudo apt remove package` – Remove package

## 🛡️ User Management
- `whoami` – Show current user
- `sudo adduser newuser` – Add user
- `sudo usermod -aG sudo newuser` – Give sudo access
- `passwd` – Change password

## 💡 Useful Tips
- Use `tab` to auto-complete commands and paths
- Use `history` to view recent commands
- Use `ctrl + r` to search previous commands
