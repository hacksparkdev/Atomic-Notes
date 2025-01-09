Tags: [[Privilege Escalation]] [[Cybersecurity]] [[Penetration Testing]] 

## Initial Enumeration 

When enumerating a Linux target we are looking for a few details: 

- **Os Version** - Knowing the version will give us an idea of what tools we can use as well as what public exploits may be available. 
- **Kernel Version** - Just like with `OS Version` there maybe be exploits that are available for a specific Kernel version. 
- **Running Services** - There may be services on the host that are misconfigured. This can be an easy win for a privilege escalation. 

### List Current Processes

```Bash
ps aux | grep root
```

#### Command Breakdown

- `ps` - Stands for `Process Status` It Provides information about currently running processes on a system. 

What `aux` Stands For

- `a:` Show processes for all users
        Displays processes from all users, not just the ones owned by the current user or running in the current terminal.

- `u:` Display user-oriented output
        Shows detailed information about each process, including the username, CPU and memory usage, and start time.

- `x:` Show processes without a controlling terminal
        Includes processes that are not attached to a terminal (e.g., background daemons).

- `|` - This pipes the command from `ps aux` into `grep root`.

### Logged in Users

```Bash
ps au
```

#### Command Breakdown

Components of ps au

- a (All Users)
        Lists processes associated with all users on the system, not just the processes owned by the current user.
        Includes processes running on terminals other than your own.
        Excludes processes that are not attached to a terminal (unlike x in aux).

- u (User-Oriented Output)
        Displays processes in a user-friendly format with detailed information such as:
            Username (USER)
            CPU usage (%CPU)
            Memory usage (%MEM)
            Process ID (PID)
            Start time (START)
            Command (COMMAND)

#### Home Directory 

```Bash
ls /home
```

We may be able to find credentials. SSH keys or ways to gain access to a Active Directory Environment. That is only if the `/home` directory is accessible.

#### User's Home Directory Contents

```Bash
ls -ls /hom/Stacy.Jenkins

```

We may be able find a readable file that could contain interesting command or configurations files. `.bash_history` would be a good file to find. 

#### SSH Directory Contents

```Bash
ls -l ~/.ssh
```

We could check for SSH keys. This could give us a fully interactive session on the host. These keys could be used to leverage other systems on the network as well. 


#### Bash History

```Bash
History
```

We can check the history for passwords passed in the shell. 

#### Sudo - List User's Privileges

```Bash
sudo -l 
```

`Sudo Privileges:` Can the user run any commands either as another user or as root? If you do not have credentials for the user, it may not be possible to leverage sudo permissions. However, often sudoer entries include NOPASSWD, meaning that the user can run the specified command without being prompted for a password. Not all commands, even we can run as root, will lead to privilege escalation. It is not uncommon to gain access as a user with full sudo privileges, meaning they can run any command as root. Issuing a simple sudo su command will immediately give you a root session.

- `Configuration Files:` Configuration files can hold a wealth of information. It is worth searching through all files that end in extensions such as .conf and .config, for usernames, passwords, and other secrets.

- `Readable Shadow File:` If the shadow file is readable, you will be able to gather password hashes for all users who have a password set. While this does not guarantee further access, these hashes can be subjected to an offline brute-force attack to recover the clear text password.

- `Password Hashes` in /etc/passwd: Occasionally, you will see password hashes directly in the /etc/passwd file. This file is readable by all users, and as with hashes in the shadow file, these can be subjected to an offline password cracking attack. This configuration, while not common, can sometimes be seen on embedded devices and routers.

#### Passwd

```Bash 
cat /ect/passwd
```


#### Cron Jobs

```Bash
ls -la /etc/cron.daily
```

Cron Jobs: Cron jobs on Linux systems are similar to Windows scheduled tasks. They are often set up to perform maintenance and backup tasks. In conjunction with other configurations such as relative paths or weak permissions, they can leverage to escalate privileges when the scheduled cron job runs.

#### File Systems & Additional Drives

```Bash
lsblk
```

`Unmounted File Systems and Additional Drives`: If you discover and can mount an additional drive or unmounted file system, you may find sensitive files, passwords, or backups that can be leveraged to escalate privileges.


#### Find Writable Directories

```Bash
find / -path /proc -prune -o -type d -perm -o+w 2>/dev/null
```

- `SETUID and SETGID Permissions:` Binaries are set with these permissions to allow a user to run a command as root, without having to grant root-level access to the user. Many binaries contain functionality that can be exploited to get a root shell.



#### Find Writable Directories

```Bash
find / -path /proc -prune -o -type d -perm -o+w 2>/dev/null
```


- `Writeable Directories:` It is important to discover which directories are writeable if you need to download tools to the system. You may discover a writeable directory where a cron job places files, which provides an idea of how often the cron job runs and could be used to elevate privileges if the script that the cron job runs is also writeable.

#### Finding Writable Files

```bash
find / -path /proc -prune -o -type f -perm -o+w 2>/dev/null
```

- `Writeable Files:` Are any scripts or configuration files world-writable? While altering configuration files can be extremely destructive, there may be instances where a minor modification can open up further access. Also, any scripts that are run as root using cron jobs can be modified slightly to append a command.

