# Silver Platter

Tags: [[Box Notes]] [[Penetration Testing]] [[Cybersecurity]]

### First Scan
#rustscan

```bash
# Nmap 7.94SVN scan initiated Sun Jan 12 09:31:54 2025 as: /usr/lib/nmap/nmap -vvv -p 22,80,8080 -A -o firstscan.txt 10.10.56.137
Nmap scan report for silverplatter.thm (10.10.56.137)
Host is up, received reset ttl 61 (0.14s latency).
Scanned at 2025-01-12 09:31:54 EST for 101s

PORT     STATE SERVICE    REASON         VERSION
22/tcp   open  ssh        syn-ack ttl 61 OpenSSH 8.9p1 Ubuntu 3ubuntu0.4 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   256 1b:1c:87:8a:fe:34:16:c9:f7:82:37:2b:10:8f:8b:f1 (ECDSA)
| ecdsa-sha2-nistp256 AAAAE2VjZHNhLXNoYTItbmlzdHAyNTYAAAAIbmlzdHAyNTYAAABBBJ0ia1tcuNvK0lfuy3Ep2dsElFfxouO3VghX5Rltu77M33pFvTeCn9t5A8NReq3felAqPi+p+/0eRRfYuaeHRT4=
|   256 26:6d:17:ed:83:9e:4f:2d:f6:cd:53:17:c8:80:3d:09 (ED25519)
|_ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIKecigNtiy6tW5ojXM3xQkbtTOwK+vqvMoJZnIxVowju
80/tcp   open  http       syn-ack ttl 61 nginx 1.18.0 (Ubuntu)
| http-methods: 
|_  Supported Methods: GET HEAD
|_http-server-header: nginx/1.18.0 (Ubuntu)
|_http-title: Hack Smarter Security
8080/tcp open  http-proxy syn-ack ttl 60
|_http-title: Error
| fingerprint-strings: 
|   FourOhFourRequest: 
|     HTTP/1.1 404 Not Found
|     Connection: close
|     Content-Length: 74
|     Content-Type: text/html
|     Date: Sun, 12 Jan 2025 14:32:01 GMT
|     <html><head><title>Error</title></head><body>404 - Not Found</body></html>
|   GenericLines, Help, Kerberos, LDAPSearchReq, LPDString, RTSPRequest, SMBProgNeg, SSLSessionReq, Socks5, TLSSessionReq, TerminalServerCookie: 

```


## SSH (22)

![[Pasted image 20250112104901.png]]
SSH is password protected. So we might be able to get a password to get in. 

## 80 (HTTP)

![[Pasted image 20250112105233.png]]
Port 80 has a website on it. if you look at the contact page you will see a password for `Silverpeas`.

![[Pasted image 20250112105607.png]]

After searching around on google i figured out what silverpeas was. I also found there was a login page on `http://silverplatter.thm:8080/silverpeas`. 

I created a worlist with `cewl`

```bash
cewl http://silverplatter.thm
```

Then i used the password file on `caido` to brute force the password. 

![[Pasted image 20250112110450.png]]

Found this password and it worked!!

![[Pasted image 20250112110519.png]]

After searching around in the notifications i noticed that the id could be changed to get into other accounts. 

![[Pasted image 20250112110819.png]]

If we change it to 6 we see a message with a ssh password. 


![[Pasted image 20250112110925.png]]

Got into the account of Tim with the password. 

wanted to look through logs for passwords. used #Grep 
```bash
grep -ir "password"
```

Found a password being passed through terminal. 

![[Pasted image 20250112111933.png]]

username: `tyler`
password: `_Zd_zx7N823/`

After logging in with tyler we see he has `sudo` privileges. And we get the root flag.
