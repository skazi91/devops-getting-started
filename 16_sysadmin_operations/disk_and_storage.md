# 💽 Disk & Storage Management – Mounts, LVM, Cleanup

Master the basics of disk usage, mounting, formatting, and cleaning up space on a Linux server.

---

## 📊 View Disk Usage
```bash
df -h           # Human-readable disk usage
lsblk           # Show block devices
mount           # Show mounted partitions
```

### 📦 Show Top Space Hogs
```bash
du -sh * | sort -rh | head -n 10
ncdu /          # Interactive CLI viewer (install first)
```

---

## 🔧 Mount a Disk
### Step 1: Identify it
```bash
lsblk
```
### Step 2: Create mount point
```bash
sudo mkdir /mnt/data
```
### Step 3: Mount manually
```bash
sudo mount /dev/sdb1 /mnt/data
```
### Step 4: Auto-mount on boot
Edit `/etc/fstab`:
```fstab
/dev/sdb1 /mnt/data ext4 defaults 0 2
```

---

## 🧹 Clean Up Disk Space
- Delete old logs:
```bash
sudo journalctl --vacuum-time=7d
sudo find /var/log -type f -mtime +7 -exec rm {} \;
```
- Remove old packages:
```bash
sudo apt autoremove
```
- Find large files:
```bash
sudo find / -type f -size +500M
```

---

## 🧰 LVM Basics
Check volumes:
```bash
sudo pvs
sudo vgs
sudo lvs
```
Resize logical volume (EXT4 only):
```bash
sudo lvextend -L +5G /dev/mapper/vg0-root
sudo resize2fs /dev/mapper/vg0-root
```

---

## 🧠 Tips
- Never edit `/etc/fstab` without testing the mount manually first
- Use `mount -a` to check fstab syntax
- Back up before resizing or formatting anything!

> 💾 Disk issues are silent killers. Monitor and clean often.
