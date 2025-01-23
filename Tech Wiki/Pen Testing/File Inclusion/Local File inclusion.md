Tags: [[Local File Inclusion (LFI)]] [[Penetration Test]] [[Cybersecurity]] [[Hack The Box]]

## Local File Inclusion 
Local File Inclusion (LFI) is a web security vulnerability that allows an attacker to include files from the server hosting the application into their own requests. This often happens due to insufficient input validation when a web application dynamically loads files based on user input.

For example, if a URL parameter like ?file=example.txt is improperly sanitized, an attacker might exploit it by providing paths like ../../etc/passwd to access sensitive files on the server. This can lead to unauthorized data exposure, code execution (if combined with upload vulnerabilities), or even full system compromise.

There are two common files that are readable on most backend server are `/etc/passwd` and `/windows/boot.ini ` on Windows. 

Here is a example of local file inclusion:
![[Pasted image 20250120115226.png]]

Here we can see that we are looking through the folders of the server that is serving the files and trying to get to the `/etc/passwd` file. This will only work if the `include()` method is using the [[absolute path]]:

```php
include($_GET['language'])
```

We can traverse back to the root and then give the absolute path we are looking for to retrieve our path. 

![[Pasted image 20250120120030.png]]

Here we can see we used `../` to go back to the root. We will only need to use as many as is necessary to get to the path. 

Sometime we may have to prepend the path with a `/`. 

```bash
http://94.237.50.242:52079/index.php?language=/../../../../etc/passwd
```

