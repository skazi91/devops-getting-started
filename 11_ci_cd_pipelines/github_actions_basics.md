# 🤖 GitHub Actions Basics – Your First CI Workflow

Automate your testing, builds, and deployments every time you push code to GitHub using GitHub Actions.

---

## ✅ What You’ll Learn
- Create a basic `.yml` workflow file
- Run tests or commands automatically on push
- Deploy or build containers after success

---

## 📁 Step 1: Create Workflow File
Inside your repo:
```bash
mkdir -p .github/workflows
nano .github/workflows/ci.yml
```
Paste this starter workflow:
```yaml
name: CI Test

on:
  push:
    branches: [ "main" ]
  pull_request:
    branches: [ "main" ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Run a hello-world test
        run: echo "✅ GitHub Actions is working!"
```
Commit and push your changes to `main` branch.

---

## 📈 Step 2: View the Action Run
1. Go to your GitHub repo
2. Click on the **Actions** tab
3. Watch the workflow run live with logs

---

## 🧪 Step 3: Add a Real Test
If you have a Python script or Bash utility:
```yaml
      - name: Run a script
        run: python3 myscript.py
```
Or test a Docker build:
```yaml
      - name: Build Docker image
        run: docker build -t my-app .
```

---

## 🔄 Automate Even More
- Auto-publish to Docker Hub
- Trigger deployment to a server
- Run security checks (e.g. CodeQL)

---

## 🔐 Pro Tips
- Keep secrets in **Settings > Secrets & variables** (e.g., `DOCKER_PASSWORD`)
- Use branches or tags to trigger separate flows
- Use caching for faster workflows

---

## 📚 Resources
- [GitHub Actions Docs](https://docs.github.com/en/actions)
- [Awesome Actions List](https://github.com/sdras/awesome-actions)
