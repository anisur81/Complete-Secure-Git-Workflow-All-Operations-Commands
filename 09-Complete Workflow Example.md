
## Part 7: Complete Workflow Example

### 7.1 Secure Daily Development Flow

```bash
# 1. Start with main branch
git checkout main
git pull --rebase origin main

# 2. Create feature branch
git checkout -b feature/secure-update

# 3. Make changes
vim app.py

# 4. Check status and changes
git status
git diff

# 5. Stage changes (with security check)
git add -p  # Interactive staging
# Check for secrets in staged changes
git diff --staged | grep -E "API_KEY|SECRET|PASSWORD"

# 6. Commit with signature
git commit -S -m "feat: Add secure update"
git show HEAD  # Verify commit

# 7. Push with force-with-lease
git push -u origin feature/secure-update --force-with-lease

# 8. Create Pull Request (via GitHub/GitLab UI)

# 9. After review, merge (via UI with required checks)

# 10. Clean up
git checkout main
git pull --rebase
git branch -d feature/secure-update

# 11. Pull latest
git pull origin main
```

### 7.2 Hotfix Emergency Workflow

```bash
# 1. Identify the issue
git log --oneline -n 10

# 2. Create hotfix branch from main
git checkout main
git pull
git checkout -b hotfix/security-fix

# 3. Apply fix
vim security-fix.py

# 4. Commit with urgent message
git add security-fix.py
git commit -S -m "HOTFIX: Critical security patch"

# 5. Test locally
python test_security.py

# 6. Push hotfix
git push -u origin hotfix/security-fix

# 7. Create PR with high priority

# 8. After merge, deploy immediately
git checkout main
git pull

# 9. Tag release
git tag -s v1.0.1-hotfix -m "Security hotfix release"
git push origin v1.0.1-hotfix
```
