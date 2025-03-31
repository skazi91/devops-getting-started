# 🛡️ Cloud Security Tips for Beginners (AWS-Focused)

Simple but powerful practices to help you secure your cloud environment — from SSH access and keys to permissions, ports, and backups.

---

## 🔐 1. Protect SSH Access
- Use **SSH keys**, not passwords
- **Disable root login** and password authentication:
```bash
sudo nano /etc/ssh/sshd_config
# Change or set:
PermitRootLogin no
PasswordAuthentication no
```
- **Allow SSH only from specific IPs** in AWS Security Groups

---

## 🔑 2. Use Least-Privilege IAM Permissions
- Avoid giving users or applications full `AdministratorAccess`
- Create **separate IAM users** for CLI/programmatic use
- Apply **custom IAM policies** only for the resources they need

---

## 🧪 3. Monitor Access and Activity
- Enable **CloudTrail** for auditing activity
- Use **AWS Config** to track config changes
- Review **IAM Access Analyzer** for unused permissions

---

## 🧰 4. Enable MFA (Multi-Factor Authentication)
- Set up MFA for:
  - Root account
  - IAM users
  - Sensitive EC2 instances (via SSH key vaulting or Bastion host)
- Use the **AWS Virtual MFA** app or Authy/Google Authenticator

---

## 🔍 5. Audit Open Ports
- Regularly check AWS Security Groups
- Only allow:
  - SSH from trusted IPs (port 22)
  - HTTP/HTTPS if you're hosting a web service
  - Deny or limit everything else

---

## 💾 6. Secure Backups
- Store encrypted backups in S3 with versioning
- Use lifecycle rules to transition to Glacier
- Protect buckets with:
  - Bucket policies
  - S3 Block Public Access settings

---

## 📜 7. Use Tags for Organization
Apply tags like:
```json
"Environment": "Production"
"Owner": "skazi91"
"Backup": "Daily"
```
This helps with cost tracking, cleanup scripts, and automation.

---

## 🚨 8. Protect Your API Keys
- Never upload credentials to GitHub!
- Use environment variables or `~/.aws/credentials`
- Rotate keys regularly and disable unused ones

---

## 🔗 Useful Tools
- [ScoutSuite](https://github.com/nccgroup/ScoutSuite) – AWS/GCP/Azure security audit
- [Prowler](https://github.com/prowler-cloud/prowler) – AWS best practice scanner
- [AWS IAM Access Analyzer](https://console.aws.amazon.com/iam/home#/access-analyzer)

---

## ✅ Keep It Simple, But Safe
Following just a few of these practices can reduce risk significantly — and show you’re thinking like a DevSecOps pro!

> ✨ Bonus: Share your cloud security hardening checklist on GitHub to help others!
