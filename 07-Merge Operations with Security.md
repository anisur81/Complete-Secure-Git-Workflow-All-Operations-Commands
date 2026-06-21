
## Part 5: Merge Operations with Security

### 5.1 Basic Merging

```bash
# Merge branch into current
git merge feature/feature-a

# Merge with commit message
git merge -m "Merge feature-a into main"

# Merge with no fast-forward
git merge --no-ff feature/feature-a

# Merge only if fast-forward possible
git merge --ff-only feature/feature-a

# Squash merge (combine all commits)
git merge --squash feature/feature-a

# Abort merge in conflict
git merge --abort

# Dry run merge
git merge --no-commit --no-ff feature/feature-a
```

### 5.2 Resolving Merge Conflicts Securely

```bash
# Show merge conflicts
git status

# View conflict details
git diff

# Show merge base
git merge-base main feature/feature-a

# Resolve conflicts manually, then:
git add resolved-file.txt
git commit -m "Resolve merge conflicts"

# Use external merge tool
git mergetool

# Continue merge after resolution
git merge --continue

# Skip merge commit
git merge --continue --no-edit
```

**Security during merges:**
```bash
# Verify changes before merge
git diff main..feature/feature-a --stat

# Check for secrets in merge
git log feature/feature-a | grep -E "secret|password"

# Verify signatures of all commits
git log --show-signature feature/feature-a

# Test build before finalizing
git merge --no-commit --no-ff feature/feature-a
# Run tests, then commit only if they pass
```
