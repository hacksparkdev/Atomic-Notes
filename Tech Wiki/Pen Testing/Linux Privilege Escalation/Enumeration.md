Tags: [[Privilege Escalation]] [[Cyber Tool]] [[Cybersecurity]] [[Penetration Testing]] 

First we will need to do some initial checks on the system to see where we are, who we are, and what we can do. 

#### Initial Commands to run 

- `whoami` - what user are we running as
- `id` - What groups does our user belong to 
- `hostname` - What is the server names, can we gather anything from the naming convention?
- `ifconfig` - or `ip a` - What subnet did we land in, does the host have additional NICs in other subnets? 
- `Sudo -l` - can our user run anything with sudo (as another user as root) without needing a password? This can sometimes be the easiest win and we can do something like `sudo su` and drop right into a root shell. 

### Check OS Release 

```Bash
cat /etc/os-release
```

This will give us information about the current OS and any information about the Kernel. 

#### Check Path

```bash
echo $PATH
```


#### Check Environment Variables

```Bash
env
```


#### Kernel Version 

```bash
uname -a
```

This will show the current Kernel Version. 


#### CPU type/version

```Bash
lscpu
```


#### Login Shells

```Bash
cat /etc/shells
```


#### Look For Drives

```Bash
lsblk
```

#### Show Mounted files 

```bash
cat /etc/fstab
```

The `/etc/fstab` file is a system configuration file in Unix-like operating systems that defines how and where disk partitions, file systems, and other storage devices are mounted.


#### Routing Tables

```Bash
route
```


#### Arp Scan

```bash
arp -a
```

Here we can see what other machines the host is communicating with. 

#### Find Information about Users and passwords

```bash
cat /ect/passwd
```

This can help us see other users on the account and any passwords that are store in this file. 



The environment enumeration also includes knowledge about the users that exist on the target system. This is because individual users are often configured during the installation of applications and services to limit the service's privileges. The reason for this is to maintain the security of the system itself. Because if a service is running with the highest privileges (root) and this is brought under control by an attacker, the attacker automatically has the highest rights over the entire system. All users on the system are stored in the /etc/passwd file. The format gives us some information, such as:

    Username
    Password
    User ID (UID)
    Group ID (GID)
    User ID info
    Home directory
    Shell

#### Pull out users from /etc/passwd file

```bash
cat /etc/passwd | cut -f1 -d: 
```


#### Check what users have login Shells

```bash
grep "*sh$" /etc/passwd
```


#### Check Groups

```bash
cat /etc/group
```

This command lists all of the groups on the system. 

#### List Interesting groups

```bash
getent group sudo 
```


#### Check Home directory 

```Bash
ls /home
```


#### Unmount file systems

```bash 
cat /etc/fstab | grep -v "#" | clumn -t
```


#### Find all hidden files

```bash
find / -type f -name ".*" -exec ls -l {} \; 2>/dev/null | grep htb-student 
```


#### All hidden Directories

```bash
find / -type d -name ".*" -ls 2>/dev/null
```


#### Temporary Files 

```bash
ls -l /tmp /var/tmp /dev/shm
```

#### Search Hack the box flag
#htbflag

```Bash
grep -ri "HTB{" / 2>/dev/null
```