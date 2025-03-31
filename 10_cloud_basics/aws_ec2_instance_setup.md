# ☁️ AWS EC2 Instance Setup – From Scratch

A beginner-friendly guide to launch your first secure Ubuntu server on AWS EC2 using the Free Tier.

---

## 🧰 Prerequisites
- AWS account ([https://aws.amazon.com/free](https://aws.amazon.com/free))
- Valid credit/debit card (only charged if you exceed free tier)
- Basic understanding of SSH (covered in our earlier guides)

---

## 📦 Step 1: Create an AWS Account
- Go to [https://aws.amazon.com/free](https://aws.amazon.com/free)
- Register and verify your email, phone, and card
- Choose **Free Tier** during setup

---

## 💻 Step 2: Launch Your EC2 Instance
1. Go to **EC2 Dashboard**
2. Click **Launch Instance**
3. Fill in:
   - **Name**: `devops-lab`
   - **AMI**: Ubuntu 22.04 LTS (Free Tier eligible)
   - **Instance Type**: `t2.micro`
   - **Key Pair**: Create new (download your `.pem` file)
   - **Network Settings**:
     - Allow **SSH (port 22)** from your IP only
     - Optional: HTTP/HTTPS
4. Click **Launch Instance** ✅

---

## 🔐 Step 3: Connect via SSH
### On Linux/macOS:
```bash
chmod 400 your-key.pem
ssh -i your-key.pem ubuntu@your-ec2-public-ip
```
### On Windows (using Git Bash or WSL):
Same as above

Or use [PuTTY](https://www.putty.org/): convert `.pem` to `.ppk` using PuTTYgen

---

## ⚙️ Step 4: First-Time Setup on the Server
```bash
sudo apt update && sudo apt upgrade -y
sudo adduser yourname
sudo usermod -aG sudo yourname
```
> Remember to copy your SSH key to this user later.

---

## 📦 Optional: Install Basic Tools
```bash
sudo apt install htop fail2ban curl ufw git unzip -y
```
Enable UFW firewall:
```bash
sudo ufw allow ssh
sudo ufw enable
```

---

## 💾 Step 5: Create a Snapshot (Optional Backup)
- In EC2 → **Elastic Block Store → Volumes**
- Select volume → **Actions → Create Snapshot**

---

## 📚 Tips & Resources
- Always stop instances when not in use to avoid charges
- Monitor usage with [AWS Billing Dashboard](https://console.aws.amazon.com/billing/home)
- [AWS EC2 Docs](https://docs.aws.amazon.com/ec2/)

---

## ✅ What’s Next?
- Install Docker, Ansible, Netdata, or other tools
- Schedule auto backups to S3
- Set up a simple web server or monitoring stack
