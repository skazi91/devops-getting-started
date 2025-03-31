# 🖥️ CLI Menu Launcher (For Network Automation Scripts)

Make your automation scripts easy to access with a Bash-based interactive menu.
Perfect for homelab, tech teams, or CLI dashboards.

---

## 📜 Example Bash Menu
```bash
#!/bin/bash

while true; do
  clear
  echo "==== Network Automation Menu ===="
  echo "1. Backup MikroTik"
  echo "2. Check Cisco Interfaces"
  echo "3. Reboot all routers"
  echo "0. Exit"
  read -p "Choose an option: " opt

  case $opt in
    1) python3 mikrotik_backup.py;;
    2) python3 cisco_interfaces.py;;
    3) python3 reboot_all.py;;
    0) exit;;
    *) echo "Invalid option"; sleep 1;;
  esac
done
```

---

## 🧠 Tips
- Keep related scripts in the same folder
- Use logging inside each Python script
- Add error handling and `ssh ping` checks before connecting

---

## 🧰 Bonus: Add FZF Launcher
Install [`fzf`](https://github.com/junegunn/fzf) and run your scripts via fuzzy finder:
```bash
select=$(ls *.sh *.py | fzf)
clear; echo "Running $select..."; ./$select
```

> 🎛️ Add color with `tput`, `figlet`, or `dialog` if you want a cooler UX!
