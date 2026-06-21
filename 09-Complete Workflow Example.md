
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
 
