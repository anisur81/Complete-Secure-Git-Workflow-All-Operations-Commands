
## Part 4: Remote Operations with Security

### 4.1 Push Operations

```bash
# Push to default remote
git push

# Push specific branch
git push origin main

# Push and set upstream
git push -u origin feature/new-feature

# Push all branches
git push --all origin

# Push tags
git push --tags

# Force push (DANGEROUS - avoid on protected branches)
git push --force

# Force push with lease (safer)
git push --force-with-lease

# Push with signed commit verification
git push --signed

# Push and delete remote branch
git push origin --delete feature/old-branch

# Dry run
git push --dry-run
```

**Push security checklist:**
```bash
# Verify push target
git remote show origin

# Check what will be pushed
git diff --stat origin/main HEAD

# Verify no secrets in commits
git log origin/main..HEAD | grep -E "password|secret"

# GPG sign all tags before push
git tag -s v1.0.0 -m "Release v1.0.0"
```

### 4.2 Pull & Fetch Operations

```bash
# Pull with merge
git pull

# Pull with rebase (cleaner history)
git pull --rebase

# Pull specific branch
git pull origin develop

# Fetch without merging
git fetch

# Fetch all remotes
git fetch --all

# Fetch specific branch
git fetch origin main

# Fetch with pruning
git fetch --prune

# Deep fetch for large repos
git fetch --depth=1

# Verify fetch
git fetch --dry-run
```

**Secure pull practices:**
```bash
# Verify before pull
git fetch origin
git log HEAD..origin/main --oneline

# Check for suspicious changes
git diff origin/main --stat

# Pull with GPG verification
git pull --verify-signatures
```
