# 🧰 AWS CLI Basics (Cross-Platform)

This guide helps you install and use the AWS Command Line Interface (CLI) to manage cloud resources like EC2, S3, IAM, and more — directly from your terminal.

---

## ✅ What You Can Do with AWS CLI
- Launch and stop EC2 instances
- Upload and manage files in S3
- List and tag resources
- Automate backups, reports, and alerts

---

## 🖥️ 1. Install AWS CLI

### Windows:
Download and install from:  
[https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-windows.html)

### macOS:
```bash
brew install awscli
```

### Linux (Debian/Ubuntu):
```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
```

---

## ⚙️ 2. Configure AWS CLI
```bash
aws configure
```
It will prompt for:
- AWS Access Key ID
- Secret Access Key
- Region (e.g., `us-east-1`)
- Output format (`json`, `text`, `table`)

Your credentials are stored securely in `~/.aws/` directory.

---

## 🧪 3. Test It Out
```bash
aws sts get-caller-identity
aws s3 ls
aws ec2 describe-instances
```

---

## 🗂️ 4. Common AWS CLI Commands
| Command | Description |
|---------|-------------|
| `aws s3 ls` | List all S3 buckets |
| `aws ec2 describe-instances` | View EC2 details |
| `aws ec2 stop-instances --instance-ids i-0123456789abcdef0` | Stop instance |
| `aws ec2 start-instances --instance-ids i-0123456789abcdef0` | Start instance |
| `aws s3 cp file.txt s3://bucket-name/` | Upload file to S3 |
| `aws iam list-users` | List IAM users |

---

## 🔐 5. Multiple Profiles
To manage multiple AWS accounts:
```bash
aws configure --profile dev
aws s3 ls --profile dev
```

---

## 📦 Extras
- Use `--output table` for pretty CLI results
- Integrate with Bash scripts, CI pipelines, or cron jobs
- Alias common commands for speed

---

## 📚 Resources
- [AWS CLI Official Docs](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-quickstart.html)
- [AWS CLI GitHub](https://github.com/aws/aws-cli)
- [Free AWS Training](https://www.aws.training/)
