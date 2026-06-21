## Part 1: Repository Setup, Initialization and Cloning

### 1.1 Starting a New Repository

**Basic initialization:**
```bash
git init                          # Start new repository
git init --bare                   # Create bare repository for central server
git init --shared=group           # Set shared permissions for team
```

**Security best practices for git init:**
```bash
# Enable GPG signing globally
git config --global commit.gpgsign true

# Set proper line endings
git config --global core.autocrlf input

# Configure safe directory (prevents security warnings)
git config --global --add safe.directory /path/to/repo

# Set default branch name
git config --global init.defaultBranch main
```

### 1.2 Cloning Repositories Securely

```bash
# Standard clone with SSH (more secure)
git clone git@github.com:username/repo.git

# Clone with HTTPS (requires token/2FA)
git clone https://github.com/username/repo.git

# Shallow clone for large repos (reduces attack surface)
git clone --depth 1 git@github.com:username/repo.git

# Clone with specific branch
git clone -b develop git@github.com:username/repo.git

# Clone with submodules
git clone --recurse-submodules git@github.com:username/repo.git
```

**Security verification:**
```bash
# Verify GPG signature of tags after clone
git tag -v <tagname>

# Verify checksum of cloned repo
git fsck --full
```
