# 💾 AWS S3 Backup Guide (For Beginners)

Learn how to back up files from your local machine, homelab, or EC2 instance to Amazon S3 using the AWS CLI.

---

## ✅ Why Use S3 for Backups?
- Durable and highly available
- Versioning and lifecycle rules
- Integrates with AWS services
- Cheap/free tier for low-volume storage

---

## 🧰 Prerequisites
- AWS account
- [S3 bucket created](https://s3.console.aws.amazon.com/s3)
- IAM user with programmatic access and `AmazonS3FullAccess` policy
- [AWS CLI installed](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html)

---

## ⚙️ 1. Configure AWS CLI
```bash
aws configure
```
You'll be prompted for:
- Access Key ID
- Secret Access Key
- Default region (e.g. `us-east-1`)
- Output format (e.g. `json`)

---

## 📤 2. Upload a File or Folder
### Upload a single file:
```bash
aws s3 cp backup.tar.gz s3://your-bucket-name/backups/
```
### Upload a full folder:
```bash
aws s3 sync /home/user/myfiles s3://your-bucket-name/myfiles-backup --delete
```
> `--delete` removes files from S3 that were deleted locally (optional)

---

## 🔁 3. Automate with Cron
Example: backup `/home/pi/projects` every day at 2am
```bash
crontab -e
```
Add:
```cron
0 2 * * * aws s3 sync /home/pi/projects s3://your-bucket-name/pi-projects
```

---

## 🗑️ 4. Versioning & Lifecycle Rules
### Enable Versioning:
- Go to your S3 bucket → Properties → Enable Versioning

### Add Lifecycle Rule:
- Move old versions to Glacier after 30 days
- Delete incomplete uploads after 7 days

---

## 🔐 5. Tips for Security
- Never expose your credentials (use environment variables or profiles)
- Rotate keys periodically
- Use minimal permissions (not full admin)

---

## 📚 Resources
- [AWS S3 Documentation](https://docs.aws.amazon.com/s3/index.html)
- [AWS CLI S3 Commands](https://docs.aws.amazon.com/cli/latest/reference/s3/)
- [AWS Free Tier](https://aws.amazon.com/free/)
