# GitHub Setup and Usage Guide (Windows + VS Code)

This document captures the complete step-by-step process followed to configure Git, connect to GitHub using SSH, and push code from a local Windows machine.

---

## 1. Verify Git Installation

```bash
git --version
```

**Purpose:** Ensure Git is installed and accessible.

---

## 2. Configure Git User

```bash
git config --global user.name "mmmanojeee"
git config --global user.email "yaragondla.manojkumar@gmail.com"
```

**Purpose:** Identify commits with your name and email.

---

## 3. Check Git Configuration

```bash
git config --list
```

**Purpose:** Validate that configuration is applied correctly.

---

## 4. Test GitHub SSH Connection (Initial)

```bash
ssh -T git@github.com
```

**Result:** `Permission denied (publickey)`

**Meaning:** GitHub is reachable, but authentication is not configured.

---

## 5. Generate SSH Key

```bash
ssh-keygen -t ed25519 -C "yaragondla.manojkumar@gmail.com"
```

**Output Files:**
- Private key: `manojssh`
- Public key: `manojssh.pub`

---

## 6. Move SSH Key to Correct Location

```bash
mv ~/Manoj_git/manojssh ~/.ssh/
mv ~/Manoj_git/manojssh.pub ~/.ssh/
```

**Purpose:** SSH expects keys inside `~/.ssh/`

---

## 7. Add SSH Key to Agent

```bash
ssh-add ~/.ssh/manojssh
```

---

## 8. Configure SSH for Custom Key

```bash
nano ~/.ssh/config
```

Add:
```
Host github.com
  HostName github.com
  User git
  IdentityFile ~/.ssh/manojssh
```

---

## 9. Add Public Key to GitHub

```bash
cat ~/.ssh/manojssh.pub
```

Copy and paste into:

https://github.com/settings/keys

---

## 10. Verify SSH Connection

```bash
ssh -T git@github.com
```

**Success Output:**
```
Hi mmmanojeee! You've successfully authenticated
```

---

## 11. Clone GitHub Repository

```bash
git clone git@github.com:mmmanojeee/azure-devops-aks-kubernetes-terraform-pipeline.git
```

---

## 12. Navigate to Repository

```bash
cd azure-devops-aks-kubernetes-terraform-pipeline
```

---

## 13. Add Changes

```bash
echo "Test change" > test.txt
```

---

## 14. Stage Changes

```bash
git add .
```

---

## 15. Commit Changes

```bash
git commit -m "Added test file"
```

---

## 16. Push to GitHub

```bash
git push
```

**Result:** Code successfully pushed to repository.

---

## Final Outcome

✅ Git installed and configured  
✅ SSH authentication setup  
✅ GitHub connected securely  
✅ Repository cloned  
✅ Changes committed and pushed  

---

## Common Commands Summary

```bash
git clone <repo>
git add .
git commit -m "message"
git push
```

---

## Key Learnings

- Git handles version control
- GitHub stores code remotely
- SSH enables secure, password-free authentication
- Git workflow: clone → modify → add → commit → push

---

## Next Steps

- Learn branching (`git checkout -b`)
- Create pull requests
- Handle merge conflicts
- Implement CI/CD pipelines

---

> Author: Manoj Kumar

