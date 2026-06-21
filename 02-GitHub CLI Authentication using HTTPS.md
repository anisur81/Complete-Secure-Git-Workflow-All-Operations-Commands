# GitHub CLI Authentication Guide

## Step-by-Step Setup

### 1. Start Authentication
```bash
gh auth login
```

### 2. Follow the Prompts

**Select Account:**
```bash
? What account do you want to log into?
> GitHub.com
```

**Choose Protocol:**
```bash
? What is your preferred protocol for Git operations?
> HTTPS
```
*Note: Choose HTTPS to avoid SSH configuration issues*

**Authentication Method:**
```bash
? How would you like to authenticate GitHub CLI?
> Login with a web browser
```

### 3. Device Code Verification

When prompted, you'll see a code like:
```bash
8FGH-1234
```

1. Open your browser and navigate to:
   ```
   https://github.com/login/device
   ```

2. Enter the displayed code

3. Authorize GitHub CLI when prompted

### 4. Verify Authentication

Check your login status:
```bash
gh auth status
```

**Expected Output:**
```bash
github.com
  ✓ Logged in to github.com account anisur81 (/home/administrator/.config/gh/hosts.yml)
  - Active account: true
  - Git operations protocol: https
  - Token: gho_************************************
  - Token scopes: 'gist', 'read:org', 'repo', 'workflow'
```

### 5. Configure Git to Use GitHub CLI

Run this command to automatically configure Git:
```bash
gh auth setup-git
```

## Benefits of This Setup

After completing these steps, you'll have:
- ✅ No manual token entry required
- ✅ No password prompts
- ✅ Seamless push/pull operations
- ✅ Automatic credential management

## Troubleshooting Tips

If you encounter issues:
- Ensure your browser is open and you can access GitHub
- Verify the device code is entered correctly
- Check your internet connection
- Make sure you have the latest version of GitHub CLI installed

---

*This guide provides a complete authentication setup for GitHub CLI, making Git operations smoother and more secure.*
