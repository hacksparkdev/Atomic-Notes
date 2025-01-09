Tags: [[SMB]] [[Penetration Testing]] [[Cybersecurity]]

### Port 
445

SMB Runs at the Application or Presentation layer of the OSI Model. SMB uses TCP/IP at a lower level to transport. SMB uses a remote server along with other resources such as printer. It is used to access files over the network. 

SMB Enabled storage on a network is called a `Share` .

## Nmap Scan

```Bash
sudo nmap -sV $target
# This will enummerate the Service. 
```

You will need `smbclient` downloaded on your system to get into the file system. 

```bash
sudo apt-get install smbclient
```


When SMB is setup sometime there is anonymous access so we will test and see if there is access. 

```Bash
smbclient -L $target


smbclient -L $target                                        
Password for [WORKGROUP\hackspark]:

	Sharename       Type      Comment
	---------       ----      -------
	ADMIN$          Disk      Remote Admin
	C$              Disk      Default share
	IPC$            IPC       Remote IPC
	WorkShares      Disk      

```

This will show us the share names. Lets see what these shares mean.

- ADMIN$ - Administrative shares are hidden network shares created by the Windows NT family of operating systems that allow system administrators to have remote access to every disk volume on a network-connected system. These shares may not be permanently deleted but may be disabled.

- C$ - Administrative share for the C:\ disk volume. This is where the operating system is hosted.

- IPC$ - The inter-process communication share. Used for inter-process communication via named pipes and is not part of the file system.

- WorkShares - Custom share

Lets Try to connect to the Custom share. 

## Connect to share

```Bash
smbclient \\\\$target\\WorkShares
```

### List all commands

```Bash
help
```

## List files

```bash
ls
```

### Download File

```Bash
get filename
```


