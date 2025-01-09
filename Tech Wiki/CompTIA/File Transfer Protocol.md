Tags: [[Tags/FTP]] [[Penetration Testing]]  [[Cybersecurity]] [[Netwroking]] #FTP [[FTP]]


## What is FTP?
**The File Transfer Protocol (FTP) is a standard communication protocol used to transfer computer files from a server to a client on a computer network. You can connect to a ftp server with a Username and password. Although you can also connect to it anonymously**

### Port Number: 21

#### SFTP - Is the secure version, Like https is to http


### Version of running Service
```Bash
Sudo nmap -sV 10.129.251.2
```

- -sV - Stands for Version 

### Installing FTP 
```Bash
Sudo apt install ftp -y 
```

### Help Command
```Bash
ftp -?
```

### Connecting to FTP 
```Bash
ftp {target_IP}
```

- If the FTP server is misconfigured we can log in with the anonymous username and hit enter on the password.
- 230  is a successful login code from ftp.

### Get Help inside of FTP 
```Bash
help
```
- This displays command we can use. 

### Get a File 
```Bash 
GET flag.txt
```

- We use the **GET** Command to get a file in the FTP server. 

### Leaving FTP
```Bash
bye
```
