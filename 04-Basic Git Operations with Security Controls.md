 
# 🔐 Part 2: Basic Git Operations with Security Controls

This section covers essential Git operations with integrated security practices to prevent accidental exposure of sensitive data.

---

## 📌 2.1 Checking Status & Working Directory

### 🔍 Basic Status Commands
```bash
git status                 # Show working directory changes
git status --short        # Compact output format
git status --branch       # Show branch information
````

### 🌐 Remote Repository Verification (Security Check)

```bash
git ls-remote --get-url   # Verify remote repository URL
git remote -v             # List all configured remotes
```

👉 Always confirm:

* Correct GitHub/GitLab repository
* No malicious or unexpected remote URL

---

## 📌 2.2 Staging Changes (git add) with Security

### 📦 Basic Staging

```bash
git add .                 # Stage all changes (use carefully)
git add file1.txt file2.js
```

### 🧠 Advanced & Safe Staging

```bash
git add -i               # Interactive staging (select changes)
git add -p               # Patch mode (stage specific chunks)
git add --dry-run .      # Preview what will be staged
```

---

### 🔐 Pre-Staging Security Checks

#### 🚨 Detect secrets before staging

```bash
git diff --staged | grep -E "API_KEY|SECRET|PASSWORD|TOKEN"
```

#### 🕵️ Scan repository for secrets (recommended tool)

```bash
1. Scan entire repository (BEST)
trufflehog git file://.

2.Scan from first commit
trufflehog git file://. --since-commit $(git rev-list --max-parents=0 HEAD)

3. Scan recent commits
trufflehog git file://. --since-commit HEAD~10

```

#### 📁 Check sensitive/untracked files

```bash
git ls-files --others --exclude-standard | grep -E "\.env|\.key|secrets"
```

---

## 📌 2.3 Committing with Security Best Practices

### 💾 Basic Commit Operations

```bash
git commit -m "message"
git commit -m "Subject" -m "Detailed description"
```

### 🔏 Secure Commit Practices

```bash
git commit -S -m "Signed commit message"   # GPG signed commit
git commit -a -m "Commit all tracked files"
git commit --amend -m "Update commit message"
git commit --amend -S --no-edit
git commit file1.txt file2.js -m "Specific file commit"
```

---

### 🛡️ Secure Commit Checklist

Before committing:

```bash
git diff --staged
```

Check for secrets:

```bash
git diff --staged | grep -E "password|secret|key|token"
```

Review last commit:

```bash
git show HEAD
```

---

## 🔐 Pre-Commit Security Hook (Mandatory for DevSecOps)

Create hook:

```bash
nano .git/hooks/pre-commit
```

Add script:

```bash
#!/bin/bash

if git diff --cached | grep -E "API_KEY|SECRET|PASSWORD|TOKEN"; then
    echo "❌ SECURITY ALERT: Potential secret detected in staged files!"
    exit 1
fi
```

Make it executable:

```bash
chmod +x .git/hooks/pre-commit
```

