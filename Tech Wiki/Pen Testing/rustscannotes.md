Tags: [[Rustscan]] [[Cybersecurity]] [[Penetration Testing]]

### **Basic Usage**
```bash
rustscan -a <IP>
```
- `-a <IP>`: Specifies the target IP address.

Example:
```bash
rustscan -a 192.168.1.1
```

---

### **Scan Specific Port Range**
```bash
rustscan -a <IP> -r <start_port>-<end_port>
```
- `-r`: Specifies the port range to scan.

Example:
```bash
rustscan -a 192.168.1.1 -r 1-1000
```
Scans ports from 1 to 1000.

---

### **Custom Number of Concurrent Scanners**
```bash
rustscan -a <IP> -b <batch_size>
```
- `-b <batch_size>`: Controls how many ports are scanned in parallel (default is `4500`).

Example:
```bash
rustscan -a 192.168.1.1 -b 1000
```
Scans ports in batches of 1000.

---

### **Scan with Custom Timeout**
```bash
rustscan -a <IP> -u <timeout>
```
- `-u <timeout>`: Sets the timeout for port scanning in milliseconds.

Example:
```bash
rustscan -a 192.168.1.1 -u 1500
```
Scans ports with a timeout of 1500 ms.

---

### **Integrate with Nmap for Service Detection**
```bash
rustscan -a <IP> -- -sC -sV
```
- `--`: Passes additional options directly to Nmap.
- `-sC`: Runs Nmap's default scripts.
- `-sV`: Attempts to determine service/version info.

Example:
```bash
rustscan -a 192.168.1.1 -- -sC -sV
```
Scans with RustScan and then runs Nmap on the detected open ports.

---

### **Exclude Specific Ports**
```bash
rustscan -a <IP> --exclude <port1,port2,...>
```
- `--exclude`: Skips the specified ports.

Example:
```bash
rustscan -a 192.168.1.1 --exclude 22,80
```
Scans all ports except `22` and `80`.

---

### **Save Output to a File**
```bash
rustscan -a <IP> -o <output_file>
```
- `-o <output_file>`: Saves the scan results to a file.

Example:
```bash
rustscan -a 192.168.1.1 -o results.txt
```

---

### **Scan All Ports**
```bash
rustscan -a <IP> -r 1-65535
```
Scans all 65,535 TCP ports.

---

### **Scan Using UDP**
RustScan itself doesn’t support UDP scanning directly. Use **Nmap** for UDP scans after identifying open ports with RustScan:
```bash
rustscan -a <IP> -- -sU
```

---

### **Verbose Output**
```bash
rustscan -a <IP> -v
```
- `-v`: Enables verbose output for more detailed information.

---

### **Run Scripts Against Open Ports**
```bash
rustscan -a <IP> -- -sC
```
This will scan open ports and run Nmap’s default scripts.

---

### **Combine with a Custom Command**
You can combine RustScan with other tools or commands:
```bash
rustscan -a <IP> -- sh -c "nmap -sV -p {port} {ip}"
```

This will pass detected ports to `nmap` for further analysis.

---

#### Save to file 

```Bash 
rustscan -a <IP> -o <output_file>
```



