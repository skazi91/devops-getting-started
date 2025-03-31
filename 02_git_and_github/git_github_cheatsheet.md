# 🧬 Git & GitHub Cheat Sheet

## 🔧 Git Configuration
- `git config --global user.name "Your Name"`
- `git config --global user.email "you@example.com"`
- `git config --list` – Show current configuration

## 📁 Repository Setup
- `git init` – Initialize a new Git repository
- `git clone https://github.com/user/repo.git` – Clone an existing repo

## 📄 Basic Workflow
- `git status` – Show modified files
- `git add file.txt` – Stage a file
- `git add .` – Stage all changes
- `git commit -m "message"` – Commit with a message
- `git log` – Show commit history

## 🔄 Branching
- `git branch` – List branches
- `git branch new-feature` – Create a new branch
- `git checkout new-feature` – Switch to a branch
- `git merge new-feature` – Merge into current branch

## 🌐 GitHub Interaction
- `git remote -v` – Show remote URL(s)
- `git remote add origin https://github.com/user/repo.git` – Add remote
- `git push -u origin main` – Push initial code
- `git pull origin main` – Pull latest from remote

## 🗑️ Undoing Changes
- `git reset file.txt` – Unstage a file
- `git checkout -- file.txt` – Discard local changes
- `git revert <commit>` – Revert a commit

## 🔐 SSH Setup (Optional but Recommended)
```bash
ssh-keygen -t rsa -b 4096 -C "you@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
cat ~/.ssh/id_rsa.pub  # Add this to GitHub SSH keys
```

## 🧪 Testing It All Together
```bash
# Quick test repo
mkdir test-repo && cd test-repo
git init
echo "Hello GitHub" > README.md
git add .
git commit -m "First commit"
# Connect to GitHub later with remote add & push
```

## 💡 Pro Tips
- Use `.gitignore` to exclude files
- Use GitHub Issues to track bugs or ideas
- Always `pull` before `push` in collaborative projects
