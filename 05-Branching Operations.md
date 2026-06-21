## Part 3: Branching Operations (Secure)

### 3.1 Branch Management

```bash
# List all branches (local)
git branch

# List all branches (local + remote)
git branch -a

# Show branch details
git branch -v

# Create new branch
git branch feature/new-feature

# Create and switch to new branch
git checkout -b feature/new-feature

# Create branch from specific commit/tag
git branch hotfix abc123
git checkout -b hotfix v1.2.3

# Delete branch (after merging)
git branch -d feature/old-branch

# Force delete (with caution)
git branch -D feature/old-branch

# Rename branch
git branch -m old-name new-name

# Set upstream branch
git branch -u origin/feature/new-feature
```

**Branch security:**
```bash
# Check branch protection
git branch --contains <commit>

# Verify branch is up to date
git fetch --dry-run

# List protected branches
git branch -r | grep -E "main|develop|release"
```

### 3.2 Switching Branches

```bash
# Switch branch
git checkout develop

# Switch using newer syntax
git switch develop

# Switch and discard local changes
git checkout --force develop

# Create new branch and switch
git checkout -b feature/new-feature

# Switch to previous branch
git checkout -

# Switch with submodules
git checkout --recurse-submodules feature/new-feature
```

**Security before switching:**
```bash
# Save uncommitted work
git stash push -m "WIP before branch switch"

# Or commit before switching
git add .
git commit -m "WIP" -S

# Verify no uncommitted changes
git status --porcelain
```
