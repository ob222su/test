# Using Different SSH Keys for Multiple GitHub Accounts

If you have multiple GitHub accounts (e.g., for different universities or work), you can use SSH to manage them separately.

---

## **1. Setting Up Your SSH Config**
Make sure you have an SSH configuration file at `~/.ssh/config` with entries like this:

```sh
Host github-bth
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_ed25519

Host github-lnu
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_lnu
```

This ensures that:
- `github-bth` uses the `id_ed25519` key.
- `github-lnu` uses the `id_rsa_lnu` key.

---

## **2. Cloning Repositories**
When cloning a repository, use the alias (`github-bth` or `github-lnu`) instead of `github.com`:

### **For BTH Account:**
```sh
git clone git@github-bth:your-username/repo.git
```

### **For LNU Account:**
```sh
git clone git@github-lnu:your-username/repo.git
```

---

## **3. Setting Remote URLs for Existing Repositories**
If you already have a repository and need to configure the correct SSH key, set the remote URL:

### **For BTH Repository:**
```sh
git remote set-url origin git@github-bth:your-username/repo.git
```

### **For LNU Repository:**
```sh
git remote set-url origin git@github-lnu:your-username/repo.git
```

---

## **4. Pulling & Pushing Code**
Once the remote is set correctly, you can pull and push as usual.

### **Pulling Updates:**
```sh
git pull origin main
```

### **Pushing Changes:**
```sh
git push origin main
```

Git will automatically use the correct SSH key based on the alias (`github-bth` or `github-lnu`).

---

## **5. Verifying SSH Connection**
To check which GitHub account you are using:

```sh
ssh -T git@github-bth
ssh -T git@github-lnu
```

This should return a message confirming authentication for the correct GitHub account.