# 🤖 Ansible Basics Guide

## 🔧 What is Ansible?
Ansible is an open-source tool for **automation**, **configuration management**, and **orchestration** using simple YAML playbooks over SSH.

---

## 🛠️ Install Ansible
### On Debian/Ubuntu:
```bash
sudo apt update
sudo apt install ansible -y
```

### On macOS:
```bash
brew install ansible
```

---

## 🧾 Inventory File Example (`hosts`)
```ini
[mikrotik]
192.168.88.1 ansible_user=admin ansible_password=admin ansible_network_os=routeros

[raspberrypi]
192.168.1.10 ansible_user=pi ansible_ssh_pass=raspberry
```

---

## 📄 Your First Playbook (`ping.yml`)
```yaml
- name: Ping all devices
  hosts: all
  gather_facts: no
  tasks:
    - name: Ping test
      ping:
```
Run it with:
```bash
ansible-playbook -i hosts ping.yml
```

---

## 📁 Sample Playbook: Install Packages on Raspberry Pi
```yaml
- name: Install tools on Raspberry Pi
  hosts: raspberrypi
  become: true
  tasks:
    - name: Install packages
      apt:
        name:
          - htop
          - git
          - docker.io
        state: present
```

---

## 🔗 Useful Modules
- `ping` – Check connectivity
- `apt`, `yum`, `dnf` – Package managers
- `copy`, `template` – Transfer files
- `command`, `shell` – Run commands
- `user`, `group` – User management

---

## 📚 Best Practices
- Use roles for large projects (`ansible-galaxy init myrole`)
- Avoid using `shell:` when a module exists (e.g. `apt`)
- Group variables in `group_vars/`
- Document playbooks clearly with `name:`

---

## 📖 Resources
- [Ansible Docs](https://docs.ansible.com/)
- [Awesome Ansible](https://github.com/jbraswell/awesome-ansible)
- `ansible-doc <module>` to see options in your terminal
