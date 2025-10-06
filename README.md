# 🚀 **GitHub Auto Deploy CLI & Collaboration Workflow**

A complete guide for setting up your project with Git, pushing it to GitHub via CLI, and collaborating with a team using branches and pull requests.

---

## 🧱 **1. Project Branch Structure**

| Branch | Purpose |
|---------|----------|
| **main** | Stable, production-ready code (live version) |
| **dev** | Development branch — where new features are merged |
| **feature/*** | Individual feature branches for each developer (e.g., `feature/login`, `feature/dashboard`) |

---

## ⚙️ **2. Setup Git and GitHub (First-Time Only)**

### ✅ Check Git installation
```bash
git --version
```

### ✅ Configure your identity
Check your name and email:
```bash
git config --global user.name
git config --global user.email
```

Set them if not configured:
```bash
git config --global user.name "Juan"
git config --global user.email "juandelacruz@gmail.com"
```

---

## 🧩 **3. Project Lead (PL) — Initial Repo Setup**

### 🔹 Step 1: Initialize Git and Create Repo via CLI
From project root folder:
```bash
git init
git add .
git commit -m "Initial commit"
gh repo create php-mvc-boilerplate-2025 --public --source=. --remote=origin
git branch -M main
git push -u origin main
```

### 🔹 Step 2: Create `dev` Branch (for all development work)
```bash
git checkout main
git pull origin main  # Ensure latest version
git checkout -b dev
git push origin dev
```

---

## 👨‍💻 **4. Developer Setup (For Jayson or Others)**

### 🔹 Step 1: Clone the repository
```bash
git clone https://github.com/jeromebernante/php-mvc-boilerplate-2025.git
cd php-mvc-boilerplate-2025
code .
```

### 🔹 Step 2: Switch to `dev` branch
```bash
git checkout dev
git pull origin dev
```

### 🔹 Step 3: Create a feature branch
Each developer creates their own branch:
```bash
git checkout -b feature/login
```

Work on their changes (via VS Code or any editor), then commit:
```bash
git add .
git commit -m "Add login page feature"
git push -u origin feature/login
```

---

## 🔁 **5. Creating a Pull Request (PR)**

1. Go to your repo on **GitHub**
2. Click **Pull Requests → New Pull Request**
3. Set:
   - **Base branch:** `dev`
   - **Compare branch:** your `feature/...` branch  
4. Add title + short description  
5. Assign reviewers (PL or teammates)  

---

## 🧠 **6. Code Review & Merging (For PL & Reviewers)**

1. Go to **Files Changed** tab  
2. Review code, add comments, or request changes  
3. Approve when ready  
4. Click **Merge Pull Request → Confirm Merge**

After merging:
```bash
# delete the merged branch locally
git branch -D feature/login

# delete from GitHub as well
git push origin --delete feature/login
```

---

## 🔄 **7. Syncing After Merge (For All Devs)**

Update your local dev branch:
```bash
git checkout dev
git pull origin dev
```

Then you can start your next task:
```bash
git checkout -b feature/dashboard
```

---

## 🧹 **8. .gitignore (Recommended for PHP Projects)**

To keep your repo clean:
```
/vendor/
/.env/
/node_modules/
/storage/
/bootstrap/cache/
/.vscode/
```

Commit once:
```bash
git add .gitignore
git commit -m "Add .gitignore for PHP project"
git push
```

---

## 🪄 **9. (Optional) Automation Script — Create Repo + Push**

For future projects, create a bash script `create-git-repo.sh`:

```bash
#!/bin/bash
# Usage: ./create-git-repo.sh repo-name
REPO=$1

git init
git add .
git commit -m "Initial commit"
gh repo create $REPO --public --source=. --remote=origin
git branch -M main
git push -u origin main
```
