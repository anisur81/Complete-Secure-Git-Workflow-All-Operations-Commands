
## Part 6: Viewing History & Changes

### 6.1 Log & History

```bash
# Basic log
git log

# Compact one-line log
git log --oneline

# Graph view (essential for branching)
git log --oneline --graph

# Full graph with all branches
git log --oneline --graph --all

# Show commits with GPG signatures
git log --show-signature

# Show recent commits
git log -n 10

# Log with statistics
git log --stat

# Search commits
git log --grep="bugfix"

# Log with date range
git log --since="2 weeks ago"

# Log affecting specific file
git log -- file.txt

# Show who changed what
git log -p
```
