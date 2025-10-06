# 🚀 GitHub Auto Deploy CLI & Collaboration Workflow

A complete guide for setting up your project with Git, pushing it to GitHub via CLI, and collaborating with a team using branches and pull requests.

---

## 🧰 1. Installation & First-Time Setup

### ✅ Install Git
1. Go to 👉 https://git-scm.com/downloads
2. Download and install Git
3. During installation:
   - Choose “Use Git from Git Bash only”
   - Choose “Checkout as-is, commit Unix-style line endings”
4. Verify installation:
   ```bash
   git --version
   ```

---

### ✅ Install GitHub CLI (gh)
1. Download from 👉 https://cli.github.com/
2. Run the installer
3. Verify installation:
   ```bash
   gh --version
   ```
4. Authenticate your GitHub account:
   ```bash
   gh auth login
   ```
   - Select GitHub.com
   - Choose HTTPS
   - Choose Yes to authenticate with your browser

✅ You’re now connected to your GitHub account!

---

### ✅ (Optional) Install Visual Studio Code
1. Download from 👉 https://code.visualstudio.com/
2. Open your project:
   ```bash
   code .
   ```

---

### ✅ Configure Git Identity
Check your current config:
```bash
git config --global user.name
git config --global user.email
```

If not set, configure them:
```bash
git config --global user.name "Juan"
git config --global user.email "juandelacruz@gmail.com"
```

---

## 🧱 2. Project Branch Structure

| Branch | Purpose |
|---------|----------|
| main | Stable, production-ready code |
| dev | Development branch where new features are merged |
| feature/* | Individual feature branches for each developer (e.g., feature/login) |

---

## 🧩 3. Project Lead (PL) — Initial Repo Setup

### 🔹 Step 1: Initialize Git and Create Repo via CLI
```bash
git init
git add .
git commit -m "Initial commit"
gh repo create php-mvc-boilerplate-2025 --public --source=. --remote=origin
git branch -M main
git push -u origin main
```

### 🔹 Step 2: Create dev Branch
```bash
git checkout main
git pull origin main
git checkout -b dev
git push origin dev
```

---

## 👨‍💻 4. Developer Setup (For Jayson or Other Collaborators)

### 🔹 Step 1: Clone the repository
```bash
git clone https://github.com/jeromebernante/php-mvc-boilerplate-2025.git
cd php-mvc-boilerplate-2025
code .
```

### 🔹 Step 2: Switch to dev branch
```bash
git checkout dev
git pull origin dev
```

### 🔹 Step 3: Create a feature branch
```bash
git checkout -b feature/login
git add .
git commit -m "Add login page feature"
git push -u origin feature/login
```

---

## 🔁 5. Creating a Pull Request (PR)
1. On GitHub, go to **Pull Requests → New Pull Request**
2. Base branch: `dev`
3. Compare branch: your `feature/...` branch
4. Add title, description, assign reviewers

---

## 🧠 6. Code Review & Merging (For PL & Reviewers)
1. Review code in **Files Changed**
2. Approve or request changes
3. When ready, click **Merge Pull Request → Confirm Merge**

After merging:
```bash
git branch -D feature/login
git push origin --delete feature/login
```

---

## 🔄 7. Sync After Merge
```bash
git checkout dev
git pull origin dev
```

Then start next feature:
```bash
git checkout -b feature/dashboard
```

---

## 🧹 8. Recommended .gitignore for PHP Projects
```
/vendor/
/.env/
/node_modules/
/storage/
/bootstrap/cache/
/.vscode/
```

Commit it:
```bash
git add .gitignore
git commit -m "Add .gitignore for PHP project"
git push
```

---

## 🪄 9. Optional: Automation Script (create-git-repo.sh)
```bash
#!/bin/bash
REPO=$1
git init
git add .
git commit -m "Initial commit"
gh repo create $REPO --public --source=. --remote=origin
git branch -M main
git push -u origin main
```

---

## ✅ End Result
- Clean branch hierarchy (main, dev, feature/*)
- Safe feature development
- Pull Request workflow for review
- All done from terminal, no manual GitHub setup!

---

### 💡 Suggested Document Title
**“GitHub Auto Deploy & Team Collaboration Workflow (CLI Method)”**
