Tags: [[FUFF]] [[Penetration Testing]] [[Directory Fuzzing]] #FUFF #Directory_fuzzing #Page_fuzzing #Recursive_fuzzing

### Simple FUFF scan. 

```bash
ffuf -w /usr/share/seclist/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u http://$target/FUZZ
```

## Finding Extensions for pages. 
Sometimes we may need to find the extension for the page such as .php .html .aspx

```bash 
ffuf -w /usr/share/seclists/Discovery/Web-Content/web-extensions.txt:FUZZ -u http://$TARGET/blog/indexFUZZ

# Here the FUZZ variable is used for the extension
```



# Page Fuzzing 

```bash
ffuf -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u http://target/FUZZ.PHP
```


# Recursive Fuzzing

```bash
ffuf -w /usr/share/seclists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -t 200 -u http://$target:8080/FUZZ -recursion -recursion-depth 1 -e .php -v  

# This will search through directories recursivly. Which means it will look thourgh sub directories.

```

# Add to Host File 
#Add_to_host_file10

```bash
sudo sh -c 'echo "SERVER_IP academy.htb" >> /etc/hosts'
```

### OR 
```Bash
echo '192.34.0.03 subdomain.domain.com' | sudo tee -a /etc/hosts
```



# Find Sub domain

```bash
# Sub domain example would be customer.inlanefreight.com
ffuf -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u https://FUZZ.inlanefreight.com/
```

# VHOST Fuzzing

```bash
ffuf -w /opt/useful/seclists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u http://academy.htb:PORT/ -H 'Host: FUZZ.academy.htb'
```


# Parameter Fuzzing - GET

```Bash
ffuf -w /opt/useful/seclists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ -u http://admin.academy.htb:PORT/admin/admin.php?FUZZ=key -fs xxx
```

First you will need to run the command without the `-fs` flag... This will give you the size. Once you get the size you can use the size. `-fs 798`

# Fuzzing - POST

```Bash
ffuf -w /opt/useful/seclists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ -u http://faculty.academy.htb:PORT/courses/linux-security.php7:PORT/admin/admin.php -X POST -d 'FUZZ=key' -H 'Content-Type: application/x-www-form-urlencoded' -fs xxx
```

# Value Fuzzing 

```Bash
ffuf -w ids.txt:FUZZ -u http://admin.academy.htb:PORT/admin/admin.php -X POST -d 'id=FUZZ' -H 'Content-Type: application/x-www-form-urlencoded' -fs xxx
```

### Use curl for value found

```Bash
curl http://admin.academy.htb:PORT/admin/admin.php -X POST -d 'id=key' -H 'Content-Type: application/x-www-form-urlencoded'
```