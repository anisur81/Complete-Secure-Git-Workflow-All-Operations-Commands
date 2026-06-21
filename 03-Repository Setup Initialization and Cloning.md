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
 

# 🔐 Git + GPG Secure Workflow (Codespaces Full Setup)

This document contains all steps used to configure Git identity, GPG signing, and signed tags in GitHub Codespaces.

---

# ⚙️ 1. Configure Git User Identity

```bash
git config --global user.name "anisur81"
git config --global user.email "anisur81@gmail.com"
```

---

# 🔍 2. Check Git Identity

```bash
git config --get user.name
git config --get user.email
```

---

# 🔎 3. Check GPG Format (Codespaces Debug)

```bash
git config --show-origin --get gpg.format
```

---

# 🔑 4. List Existing GPG Keys

```bash
gpg --list-secret-keys --keyid-format LONG
```

---

# 🆕 5. Generate New GPG Key

```bash
gpg --full-generate-key
```

---

# 🔐 6. Configure GPG Signing in Git

⚠️ Note: correct key config is `user.signingkey`

```bash
git config --global user.signkey 9952F54B2F33FCC604026598C40295A9812D998D
git config --global user.signingkey C40295A9812D998D
```

---

# ✍️ 7. Enable Commit & Tag Signing

```bash
git config --global commit.gpgsign true
git config --global tag.gpgsign true
```

---

# 📤 8. Export GPG Public Key

```bash
gpg --armor --export 9952F54B2F33FCC604026598C40295A9812D998D
```

---

# 🔧 9. Check Full Git Config (GPG Related)

```bash
git config --list --show-origin | grep -E "gpg|sign|signing|format"
```

---

# 🔑 10. Confirm GPG Key Exists

```bash
gpg --list-secret-keys --keyid-format LONG
```

---

# ⚙️ 11. Fix GPG Program (Codespaces Issue Fix)

```bash
git config --global gpg.program gpg
```

---

# 🔐 12. Configure Final Signing Key

```bash
git config --global user.signingkey C40295A9812D998D
git config --global commit.gpgsign true
git config --global tag.gpgsign true
```

---

# 🔎 13. Verify Final Config

```bash
git config --global --list | grep gpg
```

---

# 🧩 14. Fix Pinentry Issue (Codespaces Terminal Fix)

```bash
echo "pinentry-mode loopback" >> ~/.gnupg/gpg.conf
echo "allow-loopback-pinentry" >> ~/.gnupg/gpg-agent.conf
```

Restart GPG agent:

```bash
gpgconf --kill gpg-agent
gpgconf --launch gpg-agent
```

---

# 🏷️ 15. Create Signed Tag

```bash
git tag -s v1.0 -m "Signed release"
```

---

# ✔️ 16. Verify Signed Tag

```bash
git tag -v v1.0
```

---

# 📌 Summary

This setup ensures:

* ✔ Git identity configured
* ✔ GPG key created
* ✔ Git uses correct signing key
* ✔ Commit + tag signing enabled
* ✔ Codespaces pinentry issue fixed
* ✔ Signed Git tags working

---

# 🚀 Result

After this setup:

* Your commits/tags will be **cryptographically signed**
* GitHub can show **Verified badge**
* Your workflow is production-grade secure

---
 
