
# 🔐 Setup SSH Key for GitHub

## 1️⃣ Check if an SSH key already exists

```bash
ls ~/.ssh
```

Look for:

* `id_rsa` / `id_rsa.pub`
* `id_ed25519` / `id_ed25519.pub`

If none exist, continue.

---

## 2️⃣ Generate a new SSH key

### ✔ Recommended (ED25519)

```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

### Alternative (RSA 4096)

```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

Press **Enter** for default path and optional passphrase.

---

## 3️⃣ Start the SSH agent

```bash
eval "$(ssh-agent -s)"
```

---

## 4️⃣ Add the SSH key to the agent

```bash
ssh-add ~/.ssh/id_ed25519
```

---

## 5️⃣ Copy your public key

### Windows

```bash
clip < ~/.ssh/id_ed25519.pub
```

### macOS

```bash
pbcopy < ~/.ssh/id_ed25519.pub
```

### Linux

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy the entire output (starts with `ssh-ed25519`).

---

## 6️⃣ Add the SSH key to GitHub

1. Go to **GitHub → Settings → SSH & GPG Keys**
2. Click **New SSH Key**
3. Give it a name (e.g., *Laptop Key*)
4. Paste your public key
5. Save

---

## 7️⃣ Test your SSH connection

```bash
ssh -T git@github.com
```

Expected:

```
Hi username! You've successfully authenticated but GitHub does not provide shell access.
```

---

## 🎉 Completed!
