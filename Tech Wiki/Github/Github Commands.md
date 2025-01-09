Tags: [[Github]]

# Commands

#### Adding 

```bash
git add .
```

#### Committing

```bash
git commit -m "adding new file" 
```

### Pushing 

```bash
git push -u origin main
```

## Check The Current Repository URL

```
git remote -v 
```

## Set Remote repository url 

```Bash
git remote set-url origin git@gitbub.com:username/repo.git
```

## Setup SSH

The error suggests that your SSH key isn't properly set up or associated with your GitHub account. Here’s how to resolve this step by step:

---

### **1. Check if You Have an SSH Key**
Run the following command to see if an SSH key already exists:
```bash
ls ~/.ssh
```
Look for files like `id_rsa` and `id_rsa.pub`. If they exist, you already have an SSH key pair.

---

### **2. Generate an SSH Key (If Needed)**
If you don’t have an SSH key, generate one:
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
- Press `Enter` to save it in the default location (`~/.ssh/id_ed25519`).
- Set a passphrase if desired (optional).

---

### **3. Start the SSH Agent**
Ensure the SSH agent is running:
```bash
eval "$(ssh-agent -s)"
```

Add your SSH key to the agent:
```bash
ssh-add ~/.ssh/id_ed25519
```

---

### **4. Add Your SSH Key to GitHub**
1. Copy your public key:
   ```bash
   cat ~/.ssh/id_ed25519.pub
   ```
   This outputs the key. Copy everything starting with `ssh-ed25519`.

2. Go to GitHub:
   - Navigate to **Settings > SSH and GPG Keys > New SSH Key**.
   - Paste the public key and give it a title.
   - Save the key.

---

### **5. Test the SSH Connection**
Verify the connection to GitHub:
```bash
ssh -T git@github.com
```
If successful, you should see a message like:
```plaintext
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```

---

### **6. Retry the Push**
Now try pushing your changes again:
```bash
git push -u origin main
```

---

### **If You Still Encounter Issues**
1. Ensure your repository URL is using SSH, not HTTPS:
   ```bash
   git remote set-url origin git@github.com:username/repo.git
   ```
2. Double-check that you added the correct SSH key to GitHub.

Let me know if you run into further issues!
