# ☁️ Cloud VM AutoDeploy – Terraform + Ansible

Spin up a cloud VM, install Docker, and secure it using a single command. Built with Infrastructure-as-Code.

---

## 🔧 Stack
- Terraform → Provision VM (AWS EC2 or Hetzner)
- Ansible → Configure VM post-boot (Docker, firewall, users)

---

## 📁 Folder Layout
```
cloud-autodeploy/
├── main.tf
├── inventory.ini
├── playbook.yml
└── README.md
```

---

## 🗺️ Terraform (main.tf)
```hcl
provider "aws" {
  region = "us-east-1"
}

resource "aws_instance" "devbox" {
  ami = "ami-0abcdef1234567890"
  instance_type = "t2.micro"
  key_name = "devops-key"
}
```

---

## 📦 Ansible Inventory (inventory.ini)
```ini
[web]
your.public.ip ansible_user=ubuntu ansible_ssh_private_key_file=~/.ssh/devops-key.pem
```

---

## ⚙️ Ansible Playbook
```yaml
- hosts: all
  become: true
  tasks:
    - name: Install Docker
      apt:
        name: docker.io
        state: present
    - name: Enable UFW
      ufw:
        state: enabled
```

---

## 🚀 Deploy in One Command
```bash
terraform apply
ansible-playbook -i inventory.ini playbook.yml
```

> 🧠 Learn GitOps, IaC, provisioning, and config management in one shot!
