Tags: [[RDP]] [[Cybersecurity]] [[Penetration Testing]]

### Remote Desktop Protocol (RDP) - Pen Testing Notes

#### **Overview**
Remote Desktop Protocol (RDP) is a proprietary protocol developed by Microsoft that allows users to connect to another computer over a network connection. RDP enables remote control of a system with a graphical user interface (GUI), making it popular for system administration and troubleshooting.

---

### **Key Features of RDP**
- **Port**: RDP typically operates on TCP port **3389**.
- **Encryption**: RDP sessions are encrypted using protocols like TLS.
- **Multi-Session Support**: Allows multiple users to connect to a single machine.
- **Clipboard Sharing**: Transfers text, files, and resources between local and remote systems.
- **Printer and Device Redirection**: Redirects local devices (printers, drives) to the remote session.
- **Authentication**: Supports Network Level Authentication (NLA) for additional security.

---

### **Common Uses in Pen Testing**
1. **Privilege Escalation**: Misconfigured RDP settings can allow attackers to gain administrative access.
2. **Lateral Movement**: Attackers use stolen credentials to move across the network via RDP.
3. **Persistence**: Malicious users can set up scheduled tasks or registry keys to ensure RDP access remains available.
4. **Data Exfiltration**: Files and data can be copied over RDP sessions.

---

### **Potential Vulnerabilities**
1. **Weak Credentials**: Many RDP servers use weak or default credentials.
2. **Open Port 3389**: Exposing RDP to the internet makes it a common target for brute-force attacks.
3. **Lack of Network Level Authentication (NLA)**: Systems without NLA are more susceptible to attacks.
4. **BlueKeep (CVE-2019-0708)**: A critical vulnerability allowing remote code execution without authentication.
5. **Man-in-the-Middle (MitM) Attacks**: If encryption is weak, session data can be intercepted.

---

### **Pen Testing Techniques**
1. **Reconnaissance**
   - Use tools like **Nmap** to scan for open port 3389:
     ```bash
     nmap -p 3389 <target-ip>
     ```
   - Look for RDP banners to identify version and configurations:
     ```bash
     nmap --script rdp-enum-encryption -p 3389 <target-ip>
     ```

2. **Brute Force**
   - Use tools like **Hydra** or **CrackMapExec** to brute force RDP credentials:
     ```bash
     hydra -t 4 -l <username> -P <password-list> rdp://<target-ip>
     ```

3. **Exploit Vulnerabilities**
   - Test for **BlueKeep** using Metasploit or specific scripts.
   - Check for weak encryption or misconfigurations using tools like **rdp-sec-check**.

4. **Lateral Movement**
   - Use credentials harvested during the engagement to access other systems via RDP.
   - Combine with tools like **Mimikatz** to extract passwords from memory for further exploitation.

5. **Persistence**
   - Set up backdoors using registry keys or tasks:
     ```powershell
     reg add "HKLM\Software\Microsoft\Windows\CurrentVersion\Policies\System" /v fDenyTSConnections /t REG_DWORD /d 0 /f
     ```

---

### **Defensive Measures**
1. **Limit Exposure**
   - Block RDP port 3389 on the firewall for external access.
   - Use VPN or bastion hosts to access RDP internally.

2. **Strong Authentication**
   - Enforce strong password policies and multi-factor authentication (MFA).
   - Enable Network Level Authentication (NLA).

3. **Patch Management**
   - Regularly update systems to address vulnerabilities like BlueKeep.

4. **Monitoring**
   - Log and monitor RDP connection attempts for unusual activity.
   - Use tools like **Sysmon** or **Splunk** for detailed analysis.

5. **Harden RDP Configurations**
   - Limit user accounts with RDP permissions.
   - Disable clipboard and drive redirection if unnecessary.

---

### **Useful Tools**
- **Nmap**: Scanning and enumeration.
- **Metasploit**: Exploitation (e.g., BlueKeep module).
- **Hydra/CrackMapExec**: Credential brute-forcing.
- **rdp-sec-check**: Security configuration checks for RDP.
- **Mimikatz**: Credential harvesting for lateral movement.

#### xfreerdp
```bash
sudo apt-get install freerdp2-x11
```


### Connection 

```bash
xfreerdp .v: $target
```


###   Administrator Login

```bash
xfreerdp /v:$target /cert:ignore /u:Administrator
```



