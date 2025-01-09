Tags: [[Penetration Testing]] [[Service Enumeration]] #FTP

### Run a Script with Nmap to check server

```bash
nmap --script ftp-anon, ftp-syst -p 21 $TARGET
```

### Brute Force login
```bash
nmap --script ftp-brute -p 21 $TARGET
```

### Vulnerability Detection

```bash
nmap --srcipt ftp-vsftpd-backdoor -p 21 $TARGET
```
